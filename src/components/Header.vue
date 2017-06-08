<template>
  <div>
    <x-header :left-options="{showBack: false}" style="background-color:#00CC66;">{{tag}}</x-header>
  </div>
</template>
<style>
  .tabbar{
    background-color:#00CC66;
    height:50px;
    position:relative;
  }
  .search{
    position:absolute;right:5px;top:5px;z-index:999;
  }
  .title{
    text-align:center;
    margin:auto;
    color:white;
    line-height:50px;
    font-size:18px;
  }
</style>
<script>
  import { Tabbar,TabbarItem,XHeader} from 'vux'

  export default{
    name: 'AppHeader',
    data (){
        return{
          tag:'资讯',
          showMenus: false
        }
    },
    components: {
      Tabbar,
      TabbarItem,
      XHeader
    },
    methods: {
    },
  }
</script>
