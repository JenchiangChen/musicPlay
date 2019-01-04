<template>
<div class="rank">
  <scroll :data="topList" class="toplist">
    <ul>
      <li class="item" v-for="(item, index) in topList" :key="index" @click="getLink(item.id)">
        <div class="icon">
          <img width="100" height="100" v-lazy="item.picUrl" alt="">
          <span class="listen-icon"></span>
          <span class="listen-count">{{caculate(item.listenCount)}}</span>
        </div>
        <ul class="songlist">
          <span class="title">{{item.topTitle}}</span>
          <li class="song" v-for="(items, index) in item.songList" :key="index">
            <span>{{index+1}}</span>
            <span class="text">{{items.songname}}</span><span> - {{items.singername}}</span>
          </li>
        </ul>
      </li>
    </ul>
  </scroll>
  <router-view></router-view>
</div>
</template>

<script >
  import {getTopList} from 'api/rank'
  import {ERR_OK} from 'api/config'
  import Scroll from 'base/scroll/scroll'
    export default {
    data() {
      return {
        topList: []
      }
    },
      created() {
      this._getTopList()
      },
      methods: {
        _getTopList() {
          getTopList().then((res) => {
            if (res.code === ERR_OK) {
              this.topList = res.data.topList
            }
          })
        },
        caculate(val) {
          return parseInt(val / 1000) / 10 + ' 万'
        },
        getLink(val) {
          let dex = 'https://y.qq.com/w/toplist.html?ADTAG=myqq&from=myqq&channel=10007100&id=' + val + '&type=top'
          window.location.href = dex
        }
      },
      components: {
      Scroll
      }
    }
</script>

<style scoped lang="stylus" rel="stylesheet/stylus">
  @import "~common/stylus/variable"
  @import "~common/stylus/mixin"

  .rank
    position: fixed
    width: 100%
    top: 90px
    bottom: 0
    .toplist
      height: 100%
      overflow: hidden
      .item
        display: flex
        margin: 0 10px
        padding-top: 10px
        height: 100px
        &:last-child
          padding-bottom: 20px
        .icon
          flex: 0 0 100px
          width: 100px
          height: 100px
          .listen-count
            color #929292
            display block
            margin-top -20px
            font-size 12px
            margin-left 30px
          .listen-icon
            display block
            width 12px
            height 12px
            position absolute
            margin-top -21px
            margin-left 10px
            background-image url("music.png")
        .songlist
          flex: 1
          display: flex
          flex-direction: column
          justify-content: center
          padding: 0 20px
          height: 100px
          overflow: hidden
          color: #555
          font-size: $font-size-small
          .title
            font-size 18px
            color #000
            margin-bottom 5px
          .song
            no-wrap()
            line-height: 26px
            font-size 14px
            .text
              color #000
      .loading-container
        position: absolute
        width: 100%
        top: 50%
        transform: translateY(-50%)

</style>
