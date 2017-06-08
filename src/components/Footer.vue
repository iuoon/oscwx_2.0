<template>
  <div>
    <tabbar>
      <tabbar-item :link="{path:'/'}"  selected>
        <img slot="icon" src="../assets/image/ic_nav_news_normal.png">
        <img slot="icon-active" src="../assets/image/ic_nav_news_actived.png">
        <span slot="label">综合</span>
      </tabbar-item>
      <tabbar-item :link="{path:'/'}" >
        <img slot="icon" src="../assets/image/ic_nav_tweet_normal.png">
        <img slot="icon-active" src="../assets/image/ic_nav_tweet_actived.png">
        <span slot="label">动弹</span>
      </tabbar-item>
      <tabbar-item :link="{path:'/'}" >
        <img style="height:40px;width:40px;" slot="icon" src="../assets/image/ic_nav_add_normal.png">
      </tabbar-item>
      <tabbar-item :link="{path:'/'}" >
        <img slot="icon" src="../assets/image/ic_nav_discover_normal.png">
        <img slot="icon-active" src="../assets/image/ic_nav_discover_actived.png">
        <span slot="label">发现</span>
      </tabbar-item>
      <tabbar-item :link="{path:'/mysettings'}">
        <img slot="icon" src="../assets/image/ic_nav_my_normal.png">
        <img slot="icon-active" src="../assets/image/ic_nav_my_pressed.png">
        <span slot="label">我的</span>
      </tabbar-item>
    </tabbar>
  </div>
</template>
<style>
  /*.add{*/
    /*height:40px;*/
    /*width:40px;*/
  /*}*/
</style>
<script>
  import { Tabbar,TabbarItem } from 'vux'
  export default{
    name: 'AppFooter',
    components: {
      Tabbar,
      TabbarItem,
    },
    data(){
      return{
        index:0
      }
    },
    methods:{
       onclick1(){
          console.log(1);
       }
    }

  }

</script>
