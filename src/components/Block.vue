<template>
  <div class="block" v-if="showBlock" @click="stopTimer">
    Click Me
  </div>
</template>

<script>
import { setTimeout } from 'core-js';

export default {
    props:['delay'],
    data(){
        return{
            showBlock: false,
            timer: null,
            reactionTime :0
        }
    },
    mounted (){ 
        console.log("Mounted or Not")
         setTimeout(() => {
            this.showBlock=true,
            this.startTimer();
        }, this.delay)
        
    },
    methods:{
        startTimer(){
            this.timer=setInterval(()=>{
                this.reactionTime += 10
            },10)
        },
        stopTimer(){
            clearInterval(this.timer)
            this.$emit('endGame', this.reactionTime)
        }
    }
}
</script>

<style>
.block{
    width: 400px;
    border-radius: 20px;
    background-color: green;
    color: aliceblue;
    text-align: center;
    padding: 100px 0;
    margin: 40px auto;
}
</style>