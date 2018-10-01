<template>
  <div id="app">
    <v-header/>
    <div class="tab border-1px">
      <div class="tab-item">
        <router-link to="/goods" class="router-link">商品</router-link>
      </div>
      <div class="tab-item">
        <router-link to="/ratings" class="router-link">评论</router-link>
      </div>
      <div class="tab-item">
        <router-link to="/seller" class="router-link">商家</router-link>
      </div>
    </div>
    <router-view></router-view>
  </div>
</template>

<script>
import top from '@/components/top/top';
export default {
  name: 'App',
  components: {
    'v-header': top
  }
};
</script>

<style>
#app .tab{
  display: flex;
  position: relative;
  width: 100%;
  height: 40px;
  line-height: 40px;
}
.tab::after{
  display: block;
  position: absolute;
  left: 0;
  bottom: 0;
  width: 100%;
  border-top: 1px solid rgba(7, 17, 27, 0.1);
  content: ' ';
}
.tab-item{
  flex: 1;
  text-align: center;
}
.router-link{
  display: block;
  font-size: 14px;
  color: rgb(77, 85, 93);
}
.active{
  color: rgb(240, 20, 20)
}

</style>
