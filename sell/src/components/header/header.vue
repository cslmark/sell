<template>
  <div id="header">
    <div class="content-wrapper">
      <div class="bulletin-wrapper">
        <div class="avatar">
          <img width="64" height="64" :src="seller.avatar">
        </div>
        <div class="content">
          <div class="title">
            <span class="brand"></span>
            <span class="name">{{ seller.name }}</span>
          </div>
          <div class="description">
            {{ seller.description }}/{{ seller.deliveryTime }}分钟送达
          </div>
          <div v-if="seller.supports" class="support">
            <span class="icon" :class="classMap[seller.supports[0].type]"></span>
            <span class="text">{{ seller.supports[0].description }}</span>
          </div>
        </div>
        <div v-if="seller.supports" class="support-count">
          <span class="count">{{ seller.supports.length }}个</span>
          <i class="icon-keyboard_arrow_right"></i>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
  export default {
    name: 'TabHeader',
    props: {
      seller: {
        type: Object
      }
    },
    created() {
      this.classMap = ['decrease', 'discount', 'special', 'invoice', 'gurantee']
    }
  }
</script>

<style lang="less" rel="stylesheet/less">
  @import "../../common/less/index.less";

  #header {
    color: #fff;
    background: #000;
    .content-wrapper {
      position: relative;
      padding: 24px 12px 18px 24px;
      font-size: 0px;
      .avatar {
        vertical-align: top;
        display: inline-block;
        img{
          boder-radius:2px;
        }
      }
      .content {
        display: inline-block;
        margin-left: 16px;
        .title {
          margin: 2px 0 8px 0;
          .brand {
            display: inline-block;
            vertical-align: top;
            width: 30px;
            height: 18px;
            .bg-image('~./brand');
            background-size: 30px 18px;
            background-repeat: no-repeat;
          }
          .name{
            margin-left: 6px;
            font-size: 16px;
            line-height: 18px;
            font-weight: bold;
          }
        }
        .description{
          margin-bottom: 10px;
          line-height: 12px;
          font-size: 12px;
        }
        .support{
          .icon{
            vertical-align: top;
            display: inline-block;
            width: 12px;
            height: 12px;
            margin-right: 4px;
            background-size: 12px 12px;
            background-repeat: no-repeat;
            &.decrease {
              .bg-image('~./decrease_1');
            }
            &.discount{
              .bg-image('~./discount_1');
            }
            &.gurantee{
              .bg-image('~./guarantee_1');
            }
            &.invoice{
              .bg-image('~./invoice_1');
            }
            &.special{
              .bg-image('~./special_1');
            }
          }
          .text{
            font-size: 12px;
            line-height: 10px;
          }
        }
      }
      .support-count{
        position: absolute;
        right: 12px;
        bottom: 18px;
        padding: 0 8px;
        height: 24px;
        line-height: 24px;
        border-radius: 14px;
        background: rgba(0, 0,0, 0.2);
        text-align: center;
        .count{
          font-size: 10px;
          vertical-align: top;
        }
        .icon-keyboard_arrow_right{
          font-size: 10px;
        }
      }
    }
  }
</style>
