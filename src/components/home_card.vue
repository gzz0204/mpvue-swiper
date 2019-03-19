<template>
  <div class="item">
    <div class="card">
      <!-- banner图片 -->
      <div class="img_wrap">
        <image class="item_image" :src="data.coverImg"/>
      </div>
      <!-- 内容区域 -->
      <div class="cont_wrap">
        <!-- 标题 -->
        <div class="title_wrap">
          <div class="title">
            {{data.title}}
          </div>
        </div>
        <!-- 描述 -->
        <div class="desc">{{data.desc}}</div>
      </div>
    </div>
  </div>
</template>
<script>

export default {
  props: {
    data: {
      type: Object
    }
  }
}
</script>
<style lang="less" scoped>
.item{
  height: 890rpx;
  position: relative;
  .card{
    position: absolute;
    width: 625rpx;
    height: 811rpx;
    background: #fff;
    border-radius: 7rpx;
  }
}

/* 当前 swiper-item*/
.active_item .card{
  opacity: 1;
}
/* banner */
.img_wrap{
  position: relative;
  background: #303030;
  /* 图片 */
  .item_image{
    display: block;
    width: 100%;
    height: 399rpx;
    border-radius: 7rpx 7rpx 0 0;
    z-index: 5;
    opacity: 0.7;
  }
}

/* 标题出处 */
.title_wrap{
  width: 560rpx;
  height: 100rpx;
  margin: 0 auto;
  // padding-left: 130rpx;
  box-sizing: border-box;
  color: #b99c6d;
  border-bottom: 2rpx dotted #e4dcce;
  .title{
    position: relative;
    font-size: 30rpx;
    line-height: 35rpx;
    height: 70rpx;
    padding-top: 30rpx;
    overflow: hidden;
  }
}
// 描述
.desc{
  width: 554rpx;
  height: 140rpx;
  margin: 0 auto;
  color:#666666;
  font-size: 24rpx;
  line-height: 28rpx;
  overflow: hidden;
  margin-top: 21rpx;
  text-align: justify;
}
</style>
