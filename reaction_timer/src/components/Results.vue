<template>
<div>
  <p>Reaction time - {{score}} ms</p>
  <p class="rank">{{rank}}</p>
  </div>
</template>

<script>
export default {
props: ['score'],
data(){
    return{
        rank:null
    }
},
mounted(){
    if(this.score < 250 ){
        this.rank ="We have a Sonic"
    }else if (this.score < 400){
        this.rank = "Fast, but not fast enough!"
    }else{
        this.rank = "Snail pace..."
    }
}
}
</script>

<style scoped>
.rank{
    color:red
}
</style>