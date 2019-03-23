<template>
  <div id="app">
    <v-header></v-header>
    <div class="tab">
      <div class="tab-item">
        <router-link to="/goods" exact>商品</router-link>
      </div>
      <div class="tab-item">
        <router-link to="/ratings" exact>评论</router-link>
      </div>
      <div class="tab-item">
      <router-link to="/seller" exact>商家</router-link>
      </div>
    </div>
    <router-view></router-view>
  </div>
</template>

<script>
import header from '@/components/header/header'
import goods from '@/components/goods/goods'
import ratings from '@/components/ratings/ratings'
import seller from '@/components/seller/seller'

export default {
  name: 'App',
  data(){
    return {
    };
  },
  components: {
    'v-header':header,
    'goods':goods,
    'ratings':ratings,
    'seller':seller,
  }
}
</script>

<style lang="scss">
.tab{
  display: flex;
  width:100%;
  height: 40px;
  line-height: 40px;
  .tab-item{
    flex: 1;
    text-align: center;
  }
  .a{
    display: block;
    font-size: 14px;
    color:rgb(77,85,93);
  }
  .router-link-active{
    background: rgba(255,255,255,0.8);
    color: red;
  }
}
</style>
