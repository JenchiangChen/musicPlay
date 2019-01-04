<template>
  <div class="search">
    <search ref="search"></search>
    <div class="hot-box"  v-show="isclose">
      <h3 class="title">热门搜索</h3>
      <ul>
        <li @click="addsource(item.k)" class="item" v-for="(item, index) in hotKey" :key="index">
          <span>{{item.k}}</span>
        </li>
      </ul>
    </div>
  </div>
</template>

<script>
  import Search from 'base/search/search'
  import {getHotKey} from 'api/search'
  import {ERR_OK} from 'api/config'
    export default {
    data() {
      return {
        hotKey: [],
        isclose: true
      }
    },
    created() {
      this._getHotKey()
      },
      methods: {
      _getHotKey() {
        getHotKey().then(
          (res) => {
            if (res.code === ERR_OK) {
              this.hotKey = res.data.hotkey.slice(0, 10)
            }
          }
        )
      },
        addsource(source) {
        this.$refs.search.setsource(source)
        }
      },
    components: {
      Search
    }
    }
</script>

<style scoped lang="stylus" rel="stylesheet/stylus">
  .hot-box
    padding 15px 15px 10px 15px
    .title
      color rgba(0,0,0,.6)
      margin-bottom 8px
      display block
      font-size 14px
      font-weight: bold
    .item
      display: inline-block;
      font-size: 14px;
      padding: 0 10px;
      height: 30px;
      line-height: 30px;
      color: #000;
      border: 1px solid rgba(0,0,0,.6);
      border-radius: 99px;
      word-break: keep-all;
      margin-bottom: 10px;
      margin-right: 14px;
</style>
