<template>
<div>
  <div class="header" :style="'background-color:'+$store.state.color">
    <span class="header-btn" >首页</span>
    <h2 class="header-title"> {{$store.state.title}}</h2>
  </div>
  <div class="footer" :style="'background-color:'+$store.state.color">
    <ul>
      <li @click='routerLink("/")'>电影</li>
      <li @click='routerLink("music")'>音乐</li>
      <li @click='routerLink("book")'>书籍</li>
      <li @click='routerLink("photo")'>图片</li>
    </ul>
  </div>
</div>
</template>
<script>
  import store from '@/vuex/store'
  export default ({
  store,
  data(){
    return{
      bgcolor:"red"
    }
  },
  methods:{
   routerLink(path){
      this.$router.push(path);
      if(path=='book'){
        this.bgcolor='blue';
      }
    }
  }
})
</script>
<style scoped>
.header{
  height: 1rem;
  background-color:rgb(33,150,243);
  position: fixed;
  top:0;
  left: 0;
  width: 100%;
}
.header .header-title{
  color: #fff;
  font-size: 0.8rem;
  display: block;
  text-align: center;
  position: absolute;
  top:50%;
  left: 50%;
  transform: translate(-50%,-50%);
}
.header .header-btn{
  height: 1rem;
  line-height: 1rem;
  padding-left: 0.1rem;
  color: #fff;


}
  .footer{
    height: 1rem;
    background-color:rgb(33,150,243);
    position: fixed;
    bottom: 0;
    left: 0;
    width: 100%;

  }
  .footer ul{
    width: 100%;
    display: flex;
    /*flex-direction: row;*/
  }
  .footer ul li{
    color: #fff;
    flex-grow: 1;
    width: 0;
    /*float: left;*/
    /*width: 25%;*/
    text-align: center;
    /*height: 1rem;*/
    line-height: 1rem;
  }
</style>
