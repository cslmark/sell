<template>
  <div class="seller">
    <tab-header :seller="seller"></tab-header>
    <div class="tab">
      <div class="tab-item">
        <router-link to="/goods">商品</router-link>
      </div>
      <div class="tab-item">
        <router-link to="/ratings">评论</router-link>
      </div>
      <div class="tab-item">
        <router-link to="/seller">商家</router-link>
      </div>
    </div>
    <router-view></router-view>
  </div>
</template>

<script>
  import TabHeader from './header/header'
  const ERR_OK = 0
export default {
  name: 'HelloWorld',
  data () {
    return {
      msg: 'Welcome to Your Vue.js App',
      seller: {}
    }
  },
  components: {
    TabHeader
  },
  created: function () {
    this.$http.get('/api/seller').then((response) => {
      response = response.body
      if (response.errno === ERR_OK) {
        this.seller = response.data
        console.log(this.seller)
      }
    })
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style lang="less" rel="stylesheet/less">
  @import "../common/less/index.less";
  /*三等分的Tab布局建议使用flex布局*/
  #app {
    .tab {
      display: flex;
      width: 100%;
      height: 40px;
      line-height: 40px;
      /*border-bottom: 1px solid rgba(7, 17, 27, 0.1);*/
      .border-1px(rgba(7, 17, 27, 0.1));
      //.border-top-1px(red);
      .tab-item{
        flex:1;
        text-align: center;
        & > a {
          font-size: 14px;
          color:rgb(77,85,93);
          display: block;
          &.active{   // 当父元素被选中的时候
             color:rgb(240, 20 ,20);
          }
        }
      }
    }
  }
</style>
