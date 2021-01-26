<template>
  <h1>Reaction time is: {{score}} ms</h1>
  <p class="rank"><span :class="skill">{{rank}}</span></p>
</template>

<script>
export default {
    props:['score'],
    data(){
        return{
            rank:null,
            skill:''
        }
    },
    mounted(){
        if(this.score<450){
            this.rank='very Good'
            this.skill='very-good'
        }else if(this.score<550){
            this.rank='Good'
            this.skill='good'
        }else{
            this.rank='Bad'
            this.skill='bad'
        }
    }
}
</script>

<style>
    .rank{
        font-size: 1.4rem;
        font-weight: bold;
    }
    .rank .very-good{
        color: green;
    }

    .rank .good{
        color: indigo;
    }

    .rank .bad{
        color: red;
    }
</style>