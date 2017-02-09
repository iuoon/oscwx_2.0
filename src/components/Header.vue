<template>
  <tabbar class="tabbar">
    <div class="title">{{tag}}</div>
    <tabbar-item class="search">
      <img slot="icon" src="../assets/image/actionbar_search_icon.png">
    </tabbar-item>
  </tabbar>

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
  import { Tabbar,TabbarItem } from 'vux'

  export default{
    name: 'AppHeader',
    data (){
        return{
          tag:'资讯'
        }
    },
    components: {
      Tabbar,
      TabbarItem,
    },
    methods: {
    },
  }
</script>
