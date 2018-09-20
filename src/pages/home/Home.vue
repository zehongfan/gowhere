<template>
    <div>
        <Header></Header>
        <Swiper :list='swiperList'></Swiper>
        <Icons :list='iconList'></Icons>
        <Recommend :list='recommendList'></Recommend>
        <Weekend :list='weekendList'></Weekend>
    </div>
</template>

<script>
import Header from './components/Header'
import Swiper from './components/Swiper'
import Icons from './components/Icons'
import Recommend from './components/Recommend'
import Weekend from './components/Weekend'

import axios from 'axios'
import {mapState} from 'vuex'
export default{
        name:'HelloWorld',
        data(){
            return {
                swiperList:[],
                iconList:[],
                recommendList:[],
                weekendList:[],
                lastCity:''
            }
        },
        computed:{
            ...mapState(['city'])
        },
        components:{
            Header,
            Swiper,
            Icons,
            Recommend,
            Weekend
        },
        methods:{
            getHomeinfo(){
                axios.get('https://zehongfan.github.io/api/index.json?city='+this.city)
                .then((res)=>{
                    console.log(res.data)
                    this.swiperList = res.data.data.swiperList
                    this.iconList=res.data.data.iconList
                    this.recommendList=res.data.data.recommendList
                    this.weekendList=res.data.data.weekendList
                })
            }
        },
        mounted(){
            this.lastCity=this.city
            this.getHomeinfo()
        },
        activated(){
            if(this.lastCity!==this.city){
                this.lastCity=this.city
                 this.getHomeinfo()
            }
        }
        
    }

</script>