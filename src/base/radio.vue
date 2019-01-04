<template>
<div class="radio">
  <div class="list_title">电台</div>
  <ul class="list-content">
    <li class="list-item" v-for="(item, index) in radio" :key="index">
      <a class="list-main"  href="https://i.y.qq.com/v8/playsong.html?ADTAG=myqq&from=myqq&channel=10007100&songid=105309387,5126625,7112771,103848,95484,6589057,472528,102351585,861316,102338859,9077660,101128767,11859,1255742,938054,955343,8151620,101809473,1502111,105603159">
        <div class="list-media">
          <img :src="item.picUrl" alt="">
        </div>
        <div class="list-info">
          {{item.Ftitle}}
        </div>
      </a>
    </li>
  </ul>
</div>
</template>

<script>
    export default {
      name: 'radio',
      props: {
          radio: Array
      }
    }
</script>

<style scoped lang="stylus" rel="stylesheet/stylus">
  .radio
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
            img
             width 100%
          .list-info
            padding: 5px 7px 10px 5px;
            color: #000;
            font-size 14px
</style>
