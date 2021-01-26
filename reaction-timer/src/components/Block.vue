<template>
  <div class="block" v-if="showBlock" @click="stopTimer">
      Click Me
  </div>
  <div class="spinner">
   <Spinner v-if="spinner"/>
  </div>
 
  
</template>

<script>
import Spinner from './Spinner'
export default {
    components: {Spinner},
    props:['delay'],
    data(){
       return{
           showBlock:false,
           timer: null,
           reactionTimer: 0,
           spinner:false
       } 
    },
    mounted(){
        this.spinner=true
        setTimeout(()=>{
            this.showBlock=true;
            this.spinner=false
            this.startTimer();
        },this.delay)
    },
    methods:{
        startTimer(){
            this.timer=setInterval(()=>{
                this.reactionTimer+=10
           
            },10);
        },
        stopTimer(){
            clearInterval(this.timer);
            this.$emit('end',this.reactionTimer);
        }
    }
 
}
</script>

<style>
    .block{
        width: 400px;
        border-radius: 20px;
        background: #0faf87;
        color: white;
        text-align: center;
        padding: 100px 0;
        margin: 40px auto; 
        cursor: pointer; 
    }
    .spinner{
        display: flex;
        align-content: center;
        justify-content: center;
        width: 100%;
        padding: 100px 0;
        
    }
</style>