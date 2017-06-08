<template>
  <div>
    <swiper :list="imgs" auto style="width:100%;margin:0 auto;" height="120px" dots-class="custom-bottom" dots-position="center"></swiper>
    <div>
      <scroller lock-x scrollbar-y height="250px" :bounce=false :scrollbarY="false" ref="scroller">
        <div class="news-wrap-list">
          <cell v-for="x in Objlist"  :title="x.title" :link="{path: '/newsdetail',query:{id:x.id,tag:'资讯'}}" :inline-desc='x.body'>
            <img class="ic_img"  slot="icon" src="../assets/image/ic_label_today.png">
            <div>
              <span class="pubdate">{{x.pub_date}}</span>
            </div>
          </cell>
        </div>
      </scroller>
    </div>

  </div>
</template>
<style>
  .ic_img{
    position:absolute; top:10px; left: 5px;
    width:15px;
    height:15px;
  }
  .weui_cell_bd>p{
    font-size:15px;
  }
  .vux-label-desc{
    padding-right:15px;
  }
  .weui_cell_bd.weui_cell_primary{
    padding-left:5px;
  }
  .news-wrap-list {
    height: 2800px;
    overflow: hidden;
  }
  .pubdate{
    font-size:5px;

  }
</style>
<script>
  import { Group, Cell,Swiper,Scroller,Divider } from 'vux'
  import { getList } from '../utils/api'



  const imgList = [
    'http://file06.16sucai.com/2016/0222/17714c3b51079911760e5ef7fdb553f6.jpg',
    'http://pic.58pic.com/58pic/15/67/98/93C58PICjeM_1024.jpg',
    'http://file06.16sucai.com/2016/0315/1df566087c24a94cd9534bc9bc1871ff.jpg'
  ]

  const urlList = imgList.map((one, index) => ({
    url: 'javascript:',  //这里填写图片点击的链接
    img: one
  }))

  export default{
    name: 'NewsList',
    data(){
      return{
        ishow:false,
        Objlist:[],
        pageIndex:1,
        catalog:0,
        imgs:urlList,
      }
    },
    components:{
      Scroller,
      Cell,
      Group,
      Divider,
      Swiper
    },
    created () {
      this.getList()
    },
    methods:{
      async getList() {
        let data =await getList(this.pageIndex, this.catalog)
        console.log(data)
        var news_list=data.result.items;
        if(news_list.length>0){
          this.ishow=true
          for(var i=0;i<news_list.length;i++){
            var time = news_list[i].pubDate;
            var bngDate = new Date(time.replace(/-/g, "/"));
            var endDate = new Date();
            var minutes = (endDate.getTime()-bngDate.getTime())/60/1000;

            if(minutes>=60){
              minutes=minutes/60;
              var datetime=parseInt(minutes);
              if(datetime>=48){
                news_list[i].pubDate="2天前"
              }else if (datetime>=24){
                  news_list[i].pubDate="昨天"
              }else{
                news_list[i].pubDate=datetime+ "小时以前"
              }
            }else{
              var minute=parseInt(minutes);
              news_list[i].pubDate=minute+ "分钟以前"
            }
            news_list[i].title="  "+news_list[i].title;
            this.Objlist.push(news_list[i]);
          }

        }
        this.locked = false
        this.loading = false
      },
      load (uuid) {
        setTimeout(() => {
          this.getList();
          this.$broadcast('pulldown:reset', uuid)
        }, 1000)
      },
    }
  }
</script>
