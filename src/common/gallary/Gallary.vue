<template>
  <div class="container" @click="handleGallaryClick">
    <div class="wrapper">
      <swiper :options="swiperOption" >
        <swiper-slide v-for="(item,index) of imgs" :key="index"> 
          <img  class="gallary-img" :src="item" >
        </swiper-slide>
        <div class="swiper-pagination"  slot="pagination"></div>
    </swiper>
    </div>
  </div>
</template>

<script>
  export default{
    name:'Gallary',
    props:{
      imgs:{
        type:Array,
        default(){
          return ['http://img1.qunarzz.com/sight/p0/1412/66/cd09ac9548221dcc4cef8dde5913c780.water.jpg_r_800x800_bea4d4a4.jpg']
        }
      }
    },
    data(){
      return {
        swiperOption:{
        pagination: '.swiper-pagination',
        paginationType: 'fraction',
        observeParents: true,
        observer: true
        }
      }
    },
    methods:{
      handleGallaryClick(){
        this.$emit('close')
      }
    }
  }
</script>

<style lang="stylus" scoped>
  .container >>> .swiper-container
    overflow:inherit
  .container
    overflow:inherit 
    display: flex
    flex-direction: column
    justify-content: center
    z-index: 99
    position: fixed
    left: 0
    right: 0
    top: 0
    bottom: 0
    background: #000
    .wrapper
      height: 0
      width: 100%
      padding-bottom: 100%
      .gallary-img
        width: 100%
      .swiper-pagination
        color :#fff
        bottom:-1rem

</style>
