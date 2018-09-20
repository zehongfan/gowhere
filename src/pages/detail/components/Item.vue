<template>
  <div>
      <div class="ticket-list">
        <span class="ticket"></span>
        <span class="title">{{list.title}}</span>
      </div>
      <div class="ticket-list-child border-bottom" 
      v-for="(item,index) of list.ticketList" 
      :key="index"
      >
        <div>
          <div class="child-left">{{item.info}}</div>
          <div class="child-right">{{item.price}}</div>
        </div>
      </div>

      </div>
  </div>
</template>


<script>
export default {
  props:{
    list:Object
  }
}
</script>


<style lang="stylus" scoped>

  .ticket-list
    margin-top:.5rem
    height:.88rem
    background :#fff
    position: relative
    .ticket
      display: inline-block
      position:absolute
      width: .36rem
      height: .36rem
      top: .26rem
      left: .2rem
      background: url(//s.qunarzz.com/piao/image/touch/sight/detail.png) 0 -.45rem no-repeat
      margin-right: .1rem
      background-size: .4rem 3rem
    .title
      display: inline-block
      position:absolute
      height: .36rem
      line-height :.36rem
      top: .26rem
      left: .6rem
  .ticket-list-child
    position: relative
    background: #fff;
    height:.96rem
    display :flex
    flex-direction :column
    justify-content :center
    border-bottom:1px solid #ccc   
    .child-left
      position:absolute
      padding-left:.4rem
      line-height :.48rem
    .child-right
      float:right
      line-height :.48rem
      padding-right:.3rem
</style>
