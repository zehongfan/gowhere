<template>
  <div>
    <div class="banner" @click="handleBannerClick">
      <img class="banner-img" :src="bannerImg" />
      <div class="banner-info">
        <div class="banner-title">{{sightName}}</div>
        <div class="banner-number">
          <span class="iconfont banner-icon">&#xe691;</span>
          102
        </div>
      </div>
    </div>
    <Gallary 
    v-show="showGallary" 
    @close="closeGallary"
    :imgs='gallaryImgs'
    ></Gallary>
  </div>
</template>

<script>
import Gallary from 'common/gallary/Gallary'
export default {
  name:'DetailBanner',
  props:{
    sightName:String,
    bannerImg:String,
    gallaryImgs:Array
  },
  data(){
    return {
      imgs:[],
      showGallary:false
    }
  },
  methods:{
    handleBannerClick(){
      this.showGallary=true
    },
    closeGallary(){
      this.showGallary=false
    }
  },
  components:{
    Gallary
  }
}
</script>

<style lang="stylus" scoped>

  .banner
    position: relative
    height: 0
    overflow: hidden
    padding-bottom:55%
    .banner-img
      width:100%
    .banner-info
      display:flex
      position: absolute
      bottom:0
      left:0
      right:0   
      line-height: .6rem
      color: #fff  
      .banner-title
        padding-left:.2rem
        flex:1
      .banner-number
        height: .32rem
        line-height: .32rem
        margin-top: .14rem
        padding: 0 .4rem
        border-radius: .2rem
        background: rgba(0, 0, 0, .8)
        font-size: .24rem
        .banner-icon
          font-size: .24rem
</style>
