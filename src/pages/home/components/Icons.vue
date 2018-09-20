<template>

    <div class="icons">
        <swiper :options="swiperOption">
            <swiper-slide  v-for="(page,index) of pages" :key="index">
                <div class="icon"
                    v-for="item of page"
                    :key="item.id">
                    <div class="icon-img">
                    <img  class="icon-img-content" :src="item.imgUrl" />
                </div>
                    <p class="icon-desc">{{item.desc}}</p>
                </div>
            </swiper-slide>
        </swiper>
    </div>

</template>


<script>
export default {
    name:'HomeIcon',
    props:{
        list:Array
    },
    data(){
        return{
        swiperOption: {
        autoplay: false
      }
        }
    },
 computed: {
    pages () {
      const pages = []
      this.list.forEach((item, index) => {
        const page = Math.floor(index / 8)
        if (!pages[page]) {
          pages[page] = []
        }
        pages[page].push(item)
      })
      return pages
    }
  }
}
</script>

<style lang='stylus' scoped>
    .icons 
      margin-top:.2rem
      .icon  
        position :relative
        float: left
        width:25%
        padding-bottom :25%
        height :0
        .icon-img
          position :absolute
          left :0
          right:0
          top:0
          bottom 0.44rem
          .icon-img-content
            display :block
            height :100%
            margin :0 auto
        .icon-desc
          position :absolute
          left :0
          right:0
          bottom:0
          height :.44rem
          line-height :.44rem
          text-align :center
          color :black
            

</style>
