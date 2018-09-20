<template>
    <div>
      <Header></Header>
      <Search :cities='cities'></Search> 
      <List :hot='hot' 
      :cities='cities' 
      :letter='letter'></List>
      <Alphapet 
      :cities='cities'
      @change="handleLetterChange"
      ></Alphapet>
    </div>
</template>

<script>
import Header from './components/Header'
import Search from './components/Search'
import List from './components/List'
import Alphapet from './components/Alphapet'
import axios from 'axios'

export default{
  name:'City',
  components:{
    Header,
    Search,
    List,
    Alphapet
  },
  data(){
    return {
      hot:[],
      cities:{},
      letter:''
    }
  },
  methods:{
    handleLetterChange(letter){
      this.letter=letter
    },

    getCityinfo(){
      axios.get('https://zehongfan.github.io/api/city.json')
      .then((res)=>{
        this.hot=res.data.data.hotCities
        this.cities=res.data.data.cities
      })
    }
  },
  mounted(){
    this.getCityinfo()
  }
}
</script>