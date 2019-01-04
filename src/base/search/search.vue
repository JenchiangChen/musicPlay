<template>
    <div class="search-box">
      <i class="icon-search"></i>
      <input @click="close()" v-model="source" ype="text" class="box" :placeholder="placeholder">
      <i @click="clear" v-show="source" class="icon-dismiss"></i>
      <a @click="isclose = !isclose;clear()" v-show="isclose||source" class="cancel">取消</a>
    </div>
</template>

<script>
    export default {
      props: {
        placeholder: {
          default: ' 搜索歌曲、歌单、专辑 '
        }
      },
        data() {
          return {
            source: '',
            isclose: false
          }
        },
      methods: {
        clear() {
          this.source = ''
        },
        close() {
          this.isclose = true
        },
        setsource(source) {
          this.source = source
        }
      }
    }
</script>

<style scoped lang="stylus" rel="stylesheet/stylus">

  .search-box
    display: flex
    align-items: center
    box-sizing: border-box
    width: 100%
    padding: 0 6px
    height: 55px
    background: #E3E3E3
    border-radius: 6px
    .icon-search
      font-size: 26px
      color: #fff
    .box
      flex: 1
      margin: 0 5px
      padding 0  5px
      line-height: 30px
      background: $color-highlight-background
      color: #d7d7d7
      font-size: 16px
      &::placeholder
        color: #d7d7d7
    .icon-dismiss
      font-size: 16px
      color: #999999
    .cancel
      margin-left: 3px
</style>
