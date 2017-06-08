<template>
  <div id="app">
    <router-view></router-view>
    <app-footer></app-footer>
  </div>
</template>

<style lang="less">
@import '~vux/src/styles/reset';
body {
  background-color: #fbf9fe;
  line-height: 1.2;
}
</style>
<script>
  import AppFooter from './components/Footer'

  export default{
    components: {
      AppFooter
    }
  }

</script>
