<template>
  <h1>book</h1>
</template>
<script>
  import store from '@/vuex/store'

  export default({
  store,
  //  beforeRouterEnter:(to,from,next)=>{
  //     $store.commit('routeLinks' ,{
  //       color:"blue",
  //       title:"book"
  //     });
  //   next()
  // }
    created(){
      this.$store.commit('routerLinks' ,{
              color:"rgb(121,85,72)",
              title:"书籍"
            });
    }
})
</script>
<style scoped>

</style>
