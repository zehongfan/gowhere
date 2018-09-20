<template>
    <div class="recommend">
      <div class="title">热销推荐</div>
      <ul>
        <router-link tag="li" class="item" v-for="item of list" :key="item.id"
        :to="'/detail/'+item.id"
        >
          <img  class="item-img" :src="item.imgUrl" >
          <div class="item-info">
            <p class="item-title">{{item.title}}</p>
            <p class="item-desc">{{item.desc}}}</p>
            <button class="item-button">查看详情</button>
          </div>
        </router-link>
      </ul>
    </div>
</template>

<script>
export default {
    name:'HomeRecommend',
    props:{
      list:Array
    },
    data(){
      return{
      }
    }
}
</script>


<style lang="stylus" scoped>
  @import '~styles/mixins.styl'
  .recommend
    margin-top:.6rem
    .title
      margin-top :.2rem
      line-height :.8rem
      background :#eee
      text-indent: .2rem
    .item
      display:flex
      height:2.4rem
      width :100%
      .item-img
        width :2rem
        height :2rem
        padding:.2rem
      .item-info
        overflow :hidden
        .item-title
          margin-top:.26rem
          height :.44rem
          color :#212121
          font-size:.32rem
          font-szie:.32rem
          ellipsis()
        .item-desc
          margin-top :.14rem
          height:.34rem
          ellipsis()
        .item-button
          margin-top :.24rem
        
</style>
