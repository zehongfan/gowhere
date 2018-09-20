<template>
    <div class="header">
      <router-link to='/'>
        <div class="iconfont header-back">&#xe624;</div>
      </router-link>
      城市选择
    </div>
</template>

<script>

export default{
  name:'City',
}
</script>

<style  lang='stylus' scoped>
  @import "~styles/varibles.styl"
  .header
    position :relative
    text-align :center
    background :$bgColor
    height:.88rem
    line-height :.88rem
    font-szie:.32rem
    color:#fff
    .header-back
      position :absolute
      height:.88rem
      width:.8rem 
      top:0
      left:0
      color :#fff
</style>
