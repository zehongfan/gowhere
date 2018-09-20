<template>
  <div class="Detail">
    <Banner 
    :sightName='sightName'
    :bannerImg='bannerImg'
    :gallaryImgs='gallaryImgs'
    ></Banner>
    <Header></Header>
    <div v-for="(item,index) of list" :key="index">
     <Item :list='item'></Item>
    </div>
  </div>
</template>

<script>
import Banner from './components/Banner.vue'
import Header from './components/Header.vue' 
import Item from './components/Item.vue' 
import axios from 'axios'
export default {
  name:'Detail',
  components:{
    Banner,
    Header,
    Item
  },
  data(){
    return{
      sightName:'',
      bannerImg:'',
      gallaryImgs:[],
      list:[],
    }
  },
  methods:{
    getDetailInfo(){
      axios.get('https://zehongfan.github.io/api/detail.json?id='+this.$route.params.id)
    .then(this.handleGetDataSucc)
    },
     handleGetDataSucc(res){
      res = res.data
      if (res.ret && res.data) {
        const data = res.data
        console.log(data)
        this.sightName = data.sightName
        this.bannerImg = data.bannerImg
        this.gallaryImgs = data.gallaryImgs
        this.list = data.categoryList
      }
     }
  },
  mounted(){
      this.getDetailInfo()
  }
}
</script>

<style lang="stylus" scoped>
  .Detail
    height:50rem 
</style>
