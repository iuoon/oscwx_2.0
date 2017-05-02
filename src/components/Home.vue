<template>
  <div>
    <app-header></app-header>
    <tab :line-width="2"  v-model="index">
      <tab-item :selected="tag === item" v-for="item in taglist" @click="tag = item">{{item}}</tab-item>
    </tab>
    <div v-if="index === 0"><news-list></news-list></div>
    <div v-if="index === 1"><blog-list></blog-list></div>
    <div v-if="index === 2"><question-list></question-list></div>
    <div v-if="index === 3"><event-list></event-list></div>
  </div>
</template>
<style>
  /* @import '~vux/dist/vux.css'; */
  body{
    line-height: 1.2; /* 设置行间距为1.2 ,默认是1.6的太大*/
  }
</style>
<script>
  import { Tab,TabItem } from 'vux'
  import AppHeader from './Header'
  import NewsList from './NewsList'
  import BlogList from './BlogList'
  import QuestionList from './QuestionList'
  import EventList from './EventList'

  const list = () => ['资讯', '博客', '问答', '活动']

  export default {

    components: {
      Tab,
      TabItem,
      AppHeader,
      NewsList,
      BlogList,
      QuestionList,
      EventList
    },
    data () {
      return {
        tag: '资讯',
        taglist: list(),
        index:0
      }
    },
    ready () {
    },
    methods:{
    }
  }
</script>
