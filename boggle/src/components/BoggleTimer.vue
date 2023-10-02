<template>
  <div class="timerArea">
    <div class="boggleItems timerItems timerBody" @click="clickEvent">
        <div class="boggleItems timerItems"  :class="timerState">
            <!-- <input type="number" v-model="timer" placeholder="30"> -->
            {{ timer }}
        </div>
    </div>
  </div>
</template>

<script>
export default {
    name: "BoggleTimer",
    props:{
      timerState: String
    },
    data(){
      return{
        timerRange: 30,
      
      }
    },
    methods:{
      clickEvent(){
        console.log(this.timerState);
      }
    },
    computed:{
      
    }


}
</script>

<style>
  .timerItems{
    height: 400px;
    width: 50px;
    border: 1px solid #42b883;
  }

  .timerBody{
    position: relative;
  }

  .timerProgress{
    position: absolute;
    bottom:0;
    left: 0;
    right: 0;
    /* animation: progress 20s linear; */
    animation-name: progress;
    animation-duration: 30s;
    animation-timing-function: linear;
  }

  @keyframes progress {
    0%{
      background-color: #42b883;
      height: 0;
    }
    100%{
      background-color:#d23737;
      height: 100;
    }
  }
 
</style>