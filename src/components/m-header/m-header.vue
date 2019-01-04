<template>
  <div class="m-header">
    <div class="icon"></div>
    <div class="text">QQ音乐</div>
  </div>
</template>

<script>
    export default {
        name: 'm-header'
    }
</script>

<style scoped lang="stylus" rel="stylesheet/stylus">
  @import "../../common/stylus/variable"
  @import "../../common/stylus/mixin.styl"
  .m-header
    position relative
    height 44px
    margin-top 0
    color #fff
    font-size 0
    background-color #31c27c
    .icon
      display inline-block
      vertical-align top
      margin-top 6px
      margin-left 9px
      width 30px
      height 32px
      margin-right 9px
      bg-image(logo)
      background-size 30px
    .text
      display inline-block
      vertical-align top
      line-height 44px
      color #F5FCF9
      font-size $font-size-large
</style>
