<template>
    <div class="header">
        <div class="content-wrapper">
            <div class="avatar">
                <img width="64" height="64" :src="seller.avatar">
            </div>
            <div class="content">
                <div class="title">
                    <span class="brand"></span>
                    <span class="name">{{seller.name}}</span>
                </div>
                <div class="description">
                    {{seller.description}}/{{seller.deliveryTime}}分钟送达
                </div>
                <div v-if="seller.supports" class="support">
                    <span class="icon" :class="classMap[seller.supports[0].type]"></span>
                    <span class="text">{{seller.supports[0].description}}</span>
                </div>
            </div>
            <div v-if="seller.supports" class="support-count" @click="showDetail">
                <span class="count">{{seller.supports.length}}个</span>
                <i class="icon-keyboard_arrow_right"></i>
            </div>

        </div>
        <div class="bulletin-wrapper" @click="showDetail">
            <span class="bulletin-title"></span><span class="bulletin-text">{{seller.bulletin}}</span>
            <i class="icon-keyboard_arrow_right"></i>
        </div>
        <div class="backgound">
            <img :src="seller.avatar" width="100%" height="100%">
        </div>
        <div v-show="detailShow" class="detail">
            <div class="detail-wrapper clearfix">
                <div class="detail-main">

                </div>
            </div>
            <div class="detail-close icon-close" @click="detailClose"></div>
        </div>
    </div>
</template>
<script>
export default {
  name: 'header',
  props: {
    seller: {
      type: Object
    }
  },
  data () {
    return {
      detailShow: false
    };
  },
  methods: {
    showDetail () {
      this.detailShow = true;
    },
    detailClose () {
      this.detailShow = false;
    }
  },
  created () {
    this.classMap = ['decrease', 'discount', 'guarantee', 'invoice', 'special'];
  }
};
</script>
<style>
.header{
    position: relative;
    overflow: hidden;
    color: #fff;
    background-color: rgba(7, 17, 27, 0.5);
}
.content-wrapper{
    position: relative;
    padding: 24px 12px 18px 24px;
    font-size: 0;
}
.content-wrapper>.avatar{
    display: inline-block;
    vertical-align: top;
}
.content-wrapper>.avatar>img{
    border-radius: 2px;
}
.content-wrapper>.content{
    display: inline-block;
    margin-left: 16px;
    font-size: 14px;
}
.content-wrapper>.content>.title{
    margin: 2px 0 8px 0;
}
.content-wrapper>.content>.title>.brand{
    display: inline-block;
    vertical-align: top;
    width: 30px;
    height: 18px;
    background-image: url('./img/brand@2x.png');
    background-size: 30px 18px;
    background-repeat: no-repeat;
}
.content-wrapper>.content>.title>.name{
    font-size: 16px;
    font-weight: bold;
    line-height: 18px;
}
.description{
    font-size: 12px;
    font-weight: 200;
    line-height: 12px;
}
.support{
    margin: 10px 0 2px 0;
}
.support>.icon{
    display: inline-block;
    vertical-align: middle;
    width: 12px;
    height: 12px;
    background-size: 12px 12px;
    background-repeat: no-repeat;
}
.decrease{
    background-image: url('./img/decrease_1@2x.png');
}
.discount{
    background-image:url('./img/discount_1@2x.png');
}
.guarantee{
    background-image: url('./img/guarantee_1@2x.png');
}
.invoice{
    background-image: url('./img/invoice_1@2x.png');
}
.special{
    background-image: url('./img/special_1@2x.png');
}
.support>.text{
    display: inline-block;
    margin-left: 4px;
    font-size: 10px;
    font-weight: 200;
    line-height: 12px;
}
.support-count{
    position: absolute;
    right: 12px;
    bottom: 18px;
    padding: 0 8px;
    height: 24px;
    line-height: 24px;
    border-radius: 14px;
    background: rgba(0, 0, 0, 0.2);
    text-align: center;
    font-size: 10px;
    font-weight: 200;
}
.support-count>.icon-keyboard_arrow_right{
    vertical-align: middle;
    margin-left: 2px;
    line-height: 24px;
}
.bulletin-wrapper{
    position: relative;
    height: 28px;
    padding: 0 24px 0 12px;
    background-color: rgba(7, 17, 27, 0.2);
    font-size: 10px;
    white-space: nowrap;
    overflow: hidden;
    text-overflow: ellipsis;
}
.bulletin-title{
    display: inline-block;
    vertical-align: middle;
    width: 22px;
    height: 12px;
    background: url('./img/bulletin@2x.png') no-repeat;
    background-size: 22px 12px;
}
.bulletin-text{
    margin-left: 4px;
    line-height: 28px;
    font-weight: 200;
}
.bulletin-wrapper>.icon-keyboard_arrow_right{
    position: absolute;
    right: 12px;
    top: 9px;
}
.backgound{
    position: absolute;
    top: 0;
    left: 0;
    width: 100%;
    height: 100%;
    z-index: -1;
    filter: blur(10px);
}
.detail{
    position: fixed;
    top: 0;
    left: 0;
    z-index: 100;
    width: 100%;
    height: 100%;
    overflow: auto;
    background-color: rgba(7, 17, 27, 0.8);
}
.detail-wrapper{
    min-height: 100%;
}
.detail-main{
    margin-top: 64px;
    padding-bottom: 64px;
}
.detail-close{
    position: relative;
    width: 32px;
    height: 32px;
    margin: -64px auto;
    clear: both;
    font-size: 32px;
}
</style>
