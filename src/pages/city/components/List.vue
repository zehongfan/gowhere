<template>
    <div class="list" ref="wrapper">
      <div>
        <div class="area">
          <div class="title border-topbottom">当前城市</div>
          <div class="button-list">
            <div class="button-wrapper">
              <div class="button">{{this.city}}</div>
            </div>
          </div>
        </div>
        <div class="area">
          <div class="title border-topbottom">热门城市</div>
          <div class="button-list">
            <div class="button-wrapper" v-for="item of hot" :key="item.id">
              <div class="button" @click="handleCityClick(item.name)">{{item.name}}</div>
            </div>
          </div>
        </div>
        <div class="area" 
        v-for="(item,key) in cities" 
        :key="key"
        :ref="key">
          <div class="title border-topbottom" >{{key}}</div>
          <div class="item-list">
            <div class="item border-bottom" 
            v-for="city of item" 
            :key="city.id" 
            @click="handleCityClick(city.name)"
            >
              {{city.name}}
            </div>
          </div>
        </div>
      </div>
    </div>
</template>

<script>
import BScroll from 'better-scroll'
import {mapState,mapActions} from 'vuex'
export default{
  name:'CityList',
  props:{
    hot:Array,
    cities:Object,
    letter:String
  },
  mounted(){
    this.scroll=new BScroll(this.$refs.wrapper,{click:true})
  },
  methods:{
    ...mapActions(['changeCity']),
    handleCityClick(city){
      this.changeCity(city)
      this.$router.push('/')
    }
  },
  computed:{
      ...mapState(['city']),
  },
  watch:{
    letter(){
      if(this.letter){
        const element=this.$refs[this.letter][0]
        this.scroll.scrollToElement(element)
      }
    }
  }
}
</script>

<style  lang='stylus' scoped>

  @import "~styles/varibles.styl"
  .border-bottom
    &:before
      border-color:#ccc
  .border-topbottom
    &:before
      border-color:#ccc    
    &:after
      border-color:#ccc
  .list
    position: absolute
    top:1.54rem
    left :0
    right:0
    bottom:0
    overflow :hidden
    .title
      line-height :.56rem
      background :#eee
      color :#666
      padding-left:.2rem
      font-size:.26rem
    .button-list
      overflow :hidden
      padding: .1rem .6rem .1rem .1rem 
      .button-wrapper    
        width :33.33%
        float :left
        .button
          margin: .1rem 0
          padding: .1rem 0
          text-align :center
          border:.02rem solid #ccc
          border-radius :.06rem
    .item-list
      .item
        line-height: .76rem
        padding-left: .2rem
</style>
