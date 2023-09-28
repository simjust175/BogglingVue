<template>
  <div class="timerArea">
    <div class="boggleItems timerItems timerBody">
        <div class="boggleItems timerItems timerProgress ">
            <input type="number" v-model="timer" placeholder="30">
            {{ timer }}
        </div>
    </div>
  </div>
</template>

<script>
export default {
    name: "BoggleTimer",
    data(){
      return{
        timerRange: 30,
      }
    }


}
</script>

<style>
  .timerItems{
    height: 80px;
    width: 150px;
    border: 1px solid #42b883;
  }
  ::input{
    border: none;
    outline: none;
  }
</style>