<template>
  <div>
    <router-link to="/" tag="div" class="header-abs" v-show="showAbs">
      <div class="iconfont header-abs-back">&#xe624;</div>
    </router-link>
    <div 
    class="header-fixed"
    v-show="!showAbs"
    :style='opacityStyle'
    >
      <router-link to='/'>
        <div class="iconfont header-fixed-back">&#xe624;</div>
      </router-link>
      景点详情   
    </div>
  </div>
</template>


<script>
export default{
  data(){
      return{
        showAbs: true,
        opacityStyle:{
          opacity:0
        }
      }
    },
  methods:{
    handleScroll () {
      const top = document.documentElement.scrollTop || window.pageYOffset || document.body.scrollTop;
      console.log(top)
      if(top>15){
        let opacity=top/140
        opacity=opacity>1 ? 1:opacity
        this.opacityStyle={opacity:opacity}
        this.showAbs=false
      }
      else{
        this.showAbs=true
      }
    }
    },
  mounted () {
    window.addEventListener('scroll', this.handleScroll)
  },
  beforeDestroy(){
    window.removeEventListener('scroll', this.handleScroll)
  }

  }
</script>

 <style lang="stylus" scoped>
  @import "~styles/varibles.styl"
  .header-abs
    z-index :10
    position :absolute
    left :.2rem
    top: .2rem
    width: .8rem
    height :.8rem
    text-align :center
    line-height :.8rem
    border-radius :.4rem
    background :rgba(0,0,0,.8)
    .header-abs-back
      color :#fff
      font-size:.4rem
  .header-fixed
    z-index: 2
    position: fixed
    top: 0
    left: 0
    right: 0
    text-align :center
    background :$bgColor
    height:.88rem
    line-height :.88rem
    font-szie:.32rem
    color:#fff
    .header-fixed-back
      position :absolute
      height:.88rem
      width:.8rem 
      top:0
      left:0
      color :#fff
</style>
