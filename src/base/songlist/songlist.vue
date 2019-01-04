<template>
  <div class="songlist">
    <div class="list_title">热门歌单</div>
    <ul class="list-content">
      <li class="list-item" v-for="item in songlists" :key="item.id">
        <a class="list-main"  href="javascript:;" @click="getlink(item.id)">
          <div class="list-media">
            <img class="needsclick" v-lazy="item.picUrl" alt="">
            <span class="listen-icon"></span>
            <span class="listen-count">
              {{caculate(item.accessnum)}}
            </span>
            <span class="play"></span>
          </div>
          <div class="list-info">
            {{item.songListDesc}}
          </div>
          <div class="list-text">
            {{item.songListAuthor}}
          </div>
        </a>
      </li>
    </ul>
  </div>
</template>

<script>
    export default {
        props: {
          songlists: Array
        },
      methods: {
          caculate(val) {
            return parseInt(val / 1000) / 10 + ' 万'
          },
        getlink(val) {
            let dex = 'https://y.qq.com/w/taoge.html?ADTAG=myqq&from=myqq&channel=10007100&id=' + val
          window.location.href = dex
        }
      }
    }
</script>

<style scoped lang="stylus" rel="stylesheet/stylus">
  .songlist
    position relative
    margin-left:10px;
    margin-right:10px
    margin-bottom:7px
    .list_title
      font-size: 16px;
      color: #000;
      width: 100%
      height: 50px
      line-height: 50px
    .list-content
      overflow:hidden;
      margin-right:-8px;
      .list-item
        float: left;
        width: 50%;
        -webkit-box-sizing: border-box;
        padding-right: 8px;
        margin-bottom: 10px;
        overflow: hidden;
        .list-main
          display:inline-block;
          background:#fff
          .list-media
            .listen-count
              color #fff
              display block
              margin-top -20px
              font-size 12px
              margin-left 20px
            .listen-icon
              display block
              width 12px
              height 12px
              position absolute
              margin-top -20px
              margin-left 5px
              background-image url("music.png")
             .play
               display block
               width 24px
               height 24px
               position absolute
               margin-top -25px
               margin-left 150px
               background-image url("play.png")
            img
              width 100%
          .list-info
            padding: 5px 7px 5px 5px;
            color: #000;
            font-size 14px
          .list-text
            font-size: 12px
            color: #000
            padding: 5px 7px 5px 5px
    .loading-container
      position: absolute
      width: 100%
      top: 50%
      transform: translateY(-50%)
</style>
