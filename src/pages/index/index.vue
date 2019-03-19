<template>
  <div class="home_wrap">
    <swiper class="home_swiper"
      :previous-margin="previousMargin"
      :next-margin="nextMargin"
      :circular="circular"
      @change="handleChange($event)">
        <block v-for="(item, index) in datalist" :key="index">
            <swiper-item>
              <div :class="curIndex===index ? 'active_item' : 'item'" :animation="index == curIndex ? animationData : animationData2">
                <!-- 卡片项，写在子组件中 -->
                <Card :data="item" />
              </div>
            </swiper-item>
        </block>
    </swiper>
    <!-- 指示点 -->
    <div class="swiper_dot_wrap">
      <ul>
        <li v-for="(item, index) in datalist" :key="index" :class="{'active':curIndex === index}"></li>
      </ul>
    </div>
  </div>
</template>

<script>
import Card from '@/components/home_card'
export default {
  data () {
    return {
      curIndex: 0,
      datalist: [{
        coverImg: 'http://n.sinaimg.cn/sinacn20118/201/w1080h721/20190119/3311-hrvcwnk7953342.jpg',
        title: '摩尔曼斯克',
        desc: '摩尔曼斯克，北极圈内最大的城市，离芬兰也就半小时车程，整个城市才从极夜的天气中浮上来，太阳还未能升出地平线，城市只能靠云层的反射借光，一天只有几个小时的光亮，但红霞会持续一整天时间。'
      }, {
        coverImg: 'https://lh3.googleusercontent.com/IU9_NYevRO-fFjiH_hhjuxTOuDhG3cmMCWNOlnz2TBoG9jICiZevHGC0eJmvsrUwUAtbeFc=s128',
        title: '安纳托利亚往事',
        desc: '摩尔曼斯克2，北极圈内最大的城市，离芬兰也就半小时车程，整个城市才从极夜的天气中浮上来，太阳还未能升出地平线，城市只能靠云层的反射借光，一天只有几个小时的光亮，但红霞会持续一整天时间。'
      }, {
        coverImg: 'https://lh3.googleusercontent.com/xNHcyfvW2wbnSHzp9ldizNUoqhwpumx0j3QdnOlrOPH6gj4yWDif1mnaBtezpjMe9_AUKIc=s128',
        title: '圣彼得堡是另一个阿姆斯特丹',
        desc: '摩尔曼斯克3，北极圈内最大的城市，离芬兰也就半小时车程，整个城市才从极夜的天气中浮上来，太阳还未能升出地平线，城市只能靠云层的反射借光，一天只有几个小时的光亮，但红霞会持续一整天时间。'
      }],
      circular: true, // 设置衔接滑动
      previousMargin: '63rpx',
      nextMargin: '63rpx',
      animationData: {}, // 卡片放大动画
      animationData2: {} // 卡片缩小动画
    }
  },
  components: {
    Card
  },
  methods: {
    handleChange (e) {
      this.curIndex = e.mp.detail.current
      this.changeActive()
      this.changeNormal()
    },
    // 收缩
    changeNormal () {
      var animation2 = wx.createAnimation({
        duration: 500,
        timingFunction: 'ease'
      })
      this.animation2 = animation2
      animation2.scale(0.9).opacity(0.3).step()
      this.animationData2 = animation2.export()
    },
    // 展开
    changeActive () {
      var animation = wx.createAnimation({
        duration: 500,
        timingFunction: 'ease'
      })
      this.animation = animation
      animation.scale(1).opacity(1).step()
      this.animationData = animation.export()
    }
  }
}
</script>

<style lang="less" scoped>
.home_swiper {
  margin-top: 200rpx;
  position: relative;
  width: 100%;
  height: 876rpx !important;
  background: #303030;
}
.item{
  transform: scale(0.9);
  transform-origin: 50% 50% 0px;
  opacity: 0.3;
}
.active_item{
  transform: scale(1);
  opacity: 1;
}
// 指示点
.swiper_dot_wrap{
  position: absolute;
  top: 106rpx;
  right: 65rpx;
  width: 200rpx;
  height: 15rpx;
  ul{
    float: right;
    overflow: hidden;
    li{
      float: left;
      width: 15rpx;
      height: 15rpx;
      box-sizing: border-box;
      border-radius: 50%;
      border: 2rpx solid #b99c6d;
      margin-right: 15rpx;
      &:last-child{
        margin-right: 0rpx;
      }
      &.active{
        background: #b99c6d;
      }
    }
  }
}
</style>
