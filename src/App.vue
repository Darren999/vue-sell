<template>
  <div id="app">
    <v-header v-bind:seller="seller"></v-header>
    <div class="tab border-1px">
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
    <router-view v-bind:seller="seller"></router-view>
  </div>
</template>

<script>
  import header from '@/components/header/header'

  export default {
    data() {
      return {
        seller: {}
      }
    },
    created() {
      this.$http.get("/api/seller").then(response => {
        this.seller = response.body.data
        console.log(this.seller)
      }, response => {
        console.log("get data eror")
      })
    },
    components: {
      'v-header': header
    }
  }
</script>

<style lang="stylus" rel="stylesheet/stylus">
  @import "./common/stylus/mixin.styl"
  .tab
    display: flex
    width: 100%
    height: 40px
    line-height: 40px
    border-1px(rgba(7, 17, 127, 1))

    .tab-item
      flex: 1
      text-align: center

      & > a
        display: block
        font-size: 14px
        color: rgb(77, 85, 93)

        &.router-link-active
          color: rgb(240, 20, 20)
</style>
