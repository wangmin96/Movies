<template>
  <div>
    <ul>
      <li class="items" v-for="val in datas" :key="val.id">
        <div class="item-img">
          <img :src="val.img" alt="">
        </div>
        <div class="item-info">
          <h4>{{val.nm}}</h4>
          <p>{{val.ver}}</p>
          <p>主演：{{val.star}}</p>
          <p>{{val.showInfo}}</p>
        </div>
      </li>
    </ul>
    <div>
      <img src="../QQ图片20180505170320.gif" alt="" v-show="isLoading">
    </div>
    <div><h3 v-show="isEnd">到底了</h3></div>
  </div>

</template>
<script>
  import store from '@/vuex/store'
  import axios from 'axios'
  export default ({
    data(){
      return{
        datas:[],
        isLoading:false,
        isEnd:false
      }
    },
    store,
    methods:{
      getData(){
        axios.get(API_PROXY+'http://m.maoyan.com/movie/list.json?type=hot&offset='+this.datas.length+'&limit=10')
          .then((response)=> {
            this.datas = this.datas.concat(response.data.data.movies);
            this.isLoading=false;
            if(response.data.data.movies.length==0){
              this.isEnd=true;
            }
          })
          .catch((error)=>{
            console.log(error);
          });
      }
    },
    created(){
      this.$store.commit('routerLinks' ,{
        color:"rgb(33,150,243)",
        title:"电影"
      });
      this.getData();

    },
    mounted(){
      window.onscroll =() =>{
         let scrollTop=document.documentElement.scrollTop;
         let scrollHeight=document.documentElement.scrollHeight;
        let clientHeight=document.documentElement.clientHeight;
        if(scrollTop+clientHeight==scrollHeight){
          if(!this.isLoading){
            if(this.isEnd){

            }else{

              this.isLoading=true;
              this.getData()
            }
          }



        }

      }
    }
  })
</script>
<style scoped>
 .items{

   border-bottom: 1px solid #333;
   margin-bottom: .1rem;
   padding-bottom: .1rem;
   display: flex;
}
  .item-img{
    flex-grow: 1;
    width: 0;
  }
  .item-info{
    flex-grow: 2;
    width:0;
    padding-left: 0.1rem;
  }

</style>
