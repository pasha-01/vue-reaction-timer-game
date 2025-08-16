<template>
 <h1>First Mini Game Project</h1>
 <button @click="start" :disabled="isPlaying">Play</button>
 <Block v-if="isPlaying" :delay="delay" @endGame="endingGame"/>
 <Results v-if="resultShow" :score="score" />

</template>

<script>  
import Block from './components/Block.vue'
import Results from './components/Results.vue'
export default {
  name: 'App',
   components: {Block , Results },

  data(){
      return{
        isPlaying : false,
        delay :null,
        score : null,
        resultShow : false,
      }
  },
  methods:{
    start(){
      this.delay= 2000 + Math.random()*5000
      this.isPlaying=true 
      this.resultShow=false     
    },
    endingGame(timeOfReaction){
      this.score=timeOfReaction
      this.isPlaying=false
      this.resultShow=true

    }
  },
 }
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #444;
  margin-top: 60px;
}
button{
  background: green;
  color: white;
  border: none;
  padding:8px 16px ;
  border-radius: 4px;
  font-size: 16px;
  letter-spacing: 1px;
  cursor: pointer;
  margin: 10px;
}
button[disabled]{
  opacity: 0.2;
  cursor: not-allowed;
}
</style>
