<template>
    <div >
      <ul class="list">
        <li class="item" 
        v-for="item of letters" 
        :key="item" 
        :ref="item"
        @click='handleLetterClick'
        @touchstart.prevent="handleTouchStart"
        @touchmove="handleTouchMove"
        @touchend="handleTouchEnd"
        >{{item}}</li>
      </ul>
    </div>
</template>

<script>

export default{
  name:'CityAlphapet',
  props:{
    cities:Object
  },
  data(){
    return{
       touchStatus: false,
       startY:0,
       timer:null
    }
  },
  updated(){
    this.startY=this.$refs['A'][0].offsetTop
  },
  methods:{
    handleLetterClick(e){
      this.$emit('change',e.target.innerText)
    },
    handleTouchStart(){
      this.touchStatus=true
    },
    handleTouchMove(e){
      if( this.touchStatus==true){
        if(this.timer){
          clearTimeout(this.timer)
        }
        this.timer= setTimeout(()=>{
              const touchY=e.touches[0].clientY-80
              const index=Math.floor((touchY-this.startY) /20)

              if(index>=0 && index<this.letters.length)
              this.$emit('change',this.letters[index])
          },16
        )

      }

    },
    handleTouchEnd(){
         this.touchStatus=false
    }
  }, 
  computed: {
  letters () {
      const letters = []
      for (let i in this.cities) {
        letters.push(i)
      }
      return letters
    }
  },
}
</script>

<style  lang='stylus' scoped>
  @import "~styles/varibles.styl"
  .list
    position :absolute
    top:1.58rem
    right :0
    bottom:0
    width :.4rem
    display: flex
    flex-direction: column
    justify-content: center
    .item
      line-height: .4rem
      text-align: center
      color: $bgColor
</style>
