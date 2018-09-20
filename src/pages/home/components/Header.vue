<template>
    <div class="header">
        <div class="header-left">
            <div class="iconfont">&#xe624;</div>
        </div>
        <div class="header-input">
            <span class="iconfont icon_search">&#xe632;</span>
            搜素
        </div>
        <router-link to='/city'>
        <div class="header-right">{{this.city}}
            <span class="iconfont">&#xe63f;</span>
        </div>
        </router-link>
    </div>
</template>


<script>
import {mapState} from 'vuex'
export default {
    name:'HomeHeader',
    computed:{
        ...mapState(['city'])
    }
}
</script>



<style lang='stylus' scoped>
    .header
      display:flex
      line-height: .86rem
      background:#00bcd4
      .header-left
        width : .64rem
        float: left
      .header-input
        align-items:center
        display: -webkit-flex
        flex:1
        border-radius: .1rem
        height :.64rem
        height-line:.64rem
        color:#ccc
        margin-left: .2rem
        margin-top : .12rem
        padding-left: .2rem
        background :#fff  
      .header-right
        color :#fff
        padding:0 .1rem
        min-width: 1.04rem
        float:right
        text-align:center
</style>
