<template>
    <div class="star" v-bind:class="startType">
      <span v-for="itemClass in itemClasses" v-bind:class="itemClass" class="star-item"></span>
    </div>
</template>

<script>
const LENGTH = 5
const STAR_ON = 'on'
const STAR_HALF = 'half'
const STAR_OFF = 'off'
export default {
    name: "star",
    props: {
      size:{
        type: Number
      },
      score:{
        type: Number
      }
    },
    computed: {
      startType() {
        return 'star-'+this.size;
      },
      itemClasses() {
        let result = []
        let score = Math.floor(this.score)
        let hasDecimal = (this.score % 1 != 0)
        console.log("score:"+score+" hasDecimal:"+hasDecimal)
        for(let i = 0; i < score; i++){
          result.push(STAR_ON)
        }
        if (hasDecimal){
          result.push(STAR_HALF)
        }
        while(result.length < LENGTH){
          result.push(STAR_OFF)
        }

        return result;
      }
    }
}
</script>

<style lang="stylus" rel="stylesheet/stylus">
  @import "../../common/stylus/mixin.styl"

  .star
    font-size: 0
    .star-item
      display: inline-block
      background-repeat: no-repeat
    &.star-48
      .star-item
        width: 20px
        height: 20px
        margin-right: 22px
        background-size: 20px 20px
        &:last-child
          margin-right 0
        &.on
          bg-image('star48_on')
        &.half
          bg-image('star48_half')
        &.off
          bg-image('star48_off')
    &.star-36
      .star-item
        width: 15px
        height: 15px
        margin-right: 6px
        background-size: 15px 15px
        &:last-child
          margin-right 0
        &.on
          bg-image('star36_on')
        &.half
          bg-image('star36_half')
        &.off
          bg-image('star36_off')
    &.star-24
      .star-item
        width: 10px
        height: 10px
        margin-right: 2px
        background-size: 10px 10px
        &:last-child
          margin-right 0
        &.on
          bg-image('star24_on')
        &.half
          bg-image('star24_half')
        &.off
          bg-image('star24_off')
</style>
