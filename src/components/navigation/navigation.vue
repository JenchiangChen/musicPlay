<template>
    <div class="nav">
      <router-link tag="div" class="nav-item" to="/recommend">
        <span class="font-item">推荐</span>
      </router-link>
      <router-link tag="div" class="nav-item" to="/rank">
        <span class="font-item">排行榜</span>
      </router-link>
      <router-link tag="div" class="nav-item" to="/search">
        <span class="font-item">搜索</span>
      </router-link>
    </div>
</template>

<script>
    export default {
    }
</script>

<style scoped lang="stylus" rel="stylesheet/stylus">
  @import "~common/stylus/variable"
.nav
  display: flex
  height: 44px
  line-height: 44px
  font-size: $font-size-medium-x
  .nav-item
    flex 1
    text-align center
    .font-item
      padding-bottom: 5px
      color: rgba(0,0,0,.6)
    &.router-link-active
    .nav-item
      color: #31c27c
      border-bottom: 2px solid #31c27c
</style>
