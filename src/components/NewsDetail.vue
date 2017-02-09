<template>
  <div>
  <tabbar class="tabbar">
    <div class="title">{{title}}</div>
    <tabbar-item class="search">
    </tabbar-item>
  </tabbar>
  <h3 class="htitle">{{result.title}}</h3>
  <div id="content"></div>
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
  .htitle{
    text-align:center;
    margin:auto;
    color:black;
    line-height:50px;
  }
</style>
<script>
  import { Tabbar,TabbarItem} from 'vux'
  import { getNewsDetail } from '../utils/api'


  export default{
    name:'NewsDetail',
    data () {
      return {
        title: '',
        result:'',
      }
    },
    components:{
      Tabbar,
      TabbarItem,
    },
    created () {
      console.log(this.$route.query);
      this.title=this.$route.query.tag;
      this.getDetail()
    },
    methods:{
      //获取消息id,根据id到服务端请求详情
      async getDetail() {
        let data =await getNewsDetail(this.$route.query.id);
        console.log(data);
        if(data.code>=0){
          this.result=data.result;
          this.body=this.result.body;
          document.getElementById("content").innerHTML=this.body;
        }
      }
    }
  }
</script>
