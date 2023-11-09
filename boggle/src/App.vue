<template>
  <div class="cona">
  <img alt="Vue logo" class="logo" src="./assets/logo.svg" width="125" height="125" />
  <div class="mainContainer">
    <div class="refreshArea">
      <div class="refresh">
        <RefreshButton @createdList="newList" />
      </div>
    </div>
    <div class="main-area">
      <div class="boggle-board boggleItems">
        <BoggleCell class="boggle-cell" :class="shuffle" v-for="index in 16" :key="index"
         :dice-list="diceArray"
          @minimize-dice="removeDice"
          :usedDice="usedDice" />
      </div>
      <div class="timerArea">
        <BoggleTimer :timer-state="timerOn()" />
      </div>
      <div class="design circle1"></div>
      <div class="design circle2"></div>
      <div class="design circle3"></div>
    </div>
    
  </div>
</div>
</template>

<script>
import BoggleTimer from "./components/BoggleTimer.vue";
import RefreshButton from "./components/RefreshButton.vue";
import BoggleCell from "./components/BoggleCell.vue";
export default {
  components: {
    BoggleTimer,
    RefreshButton,
    BoggleCell,
  },
  data() {
    return {
      diceArray: [],
      usedDice: new Set(),
      shuffle: ""
    }
  },
  methods: {
    removeDice(randomDice) {
      this.usedDice.add(parseInt(randomDice))
    },

    timerOn() {
      return "timerProgress";
    },

    newList(list) {
      this.diceArray = list;
    }
  },
  watch:{
    diceArray(){
      this.usedDice.clear()
      this.shuffle = "shuffle"
      
    }
  }
};
</script>

<style>
:root {
  --color-primary: #42b883;
  --color-secondary-dark: #388f68;
  --border-radius: 8px;
}

.conta{
  width: 100vw;
  height: 100vh;
  overflow: hidden;
}
.boggleItems {
  border-radius: var(--border-radius);
  border: 1px #42b883 solid;
}

.logo {
  height: 100px;
  width: auto;
  position: absolute;
  top: 10px;
  left: 10px;
  z-index: -2;
  opacity: 60%;
  transition: all 0.4s ease;
}

.logo:hover{
  transform:scale(1.08);
}

.design{
  height: 1000px;
  width: 1000px;
  
  position: absolute;
  z-index: -1;
  border-radius: 50%;
  overflow: hidden;
}

.circle1{
  right: -250px;
  top: -250px;
  background: #388f6854;

}

.circle2{
  right: -550px;
  top: -550px;
  background: #388f6885;
}

.circle3{
  left: -550px;
  bottom: -550px;
  background: #388f6885;

}

.mainContainer {
  position: absolute;
  top: 50%;
  left: 50%;
  transform: translate(-50%, -50%);
  z-index: 1;
  display: flex;
  flex-direction: column-reverse;
  justify-content: space-around;
  /* width: 100%; */
}

.main-area {
  display: flex;
  gap: 25px;
}

.timerArea {
  height: 100%;
}

/* Boggle Board */
.boggle-board {
  display: grid;
  grid-template-columns: repeat(4, 1fr);
  gap: 10px;
  background-color: #42b883;
  padding: 10px;
  border-radius: 10px;
  perspective: 800px;
}

/* Boggle Cell */
.boggle-cell {
  display: flex;
  align-items: center;
  justify-content: center;
  font-size: 32px;
  font-weight: bold;
  background-color: #ffffff;
  border-radius: 5px;
  cursor: pointer;
  transform-style: preserve-3d;
  transition: transform 0.3s ease;
  position: relative;
  box-shadow: 0px 3px 6px rgba(0, 0, 0, 0.16), 0px 3px 6px rgba(0, 0, 0, 0.23);
  animation: shuffle 0.5s ease;
}

.boggle-cell::before {
  content: "";
  position: absolute;
  top: -5px;
  left: -5px;
  right: -5px;
  bottom: -5px;
  background-color: #ffffff;
  border-radius: 5px;
  transform: translateZ(-5px);
  box-shadow: 0px 0px 16px 0px rgba(0, 0, 0, 0.2);
}

.boggle-cell::after {
  content: "";
  position: absolute;
  top: -5px;
  left: -5px;
  width: 100%;
  height: 100%;
  background-color: rgba(0, 0, 0, 0.1);
  border-radius: 5px;
  transform: translateY(5px);
  transition: transform 0.3s ease;
  box-shadow: 0px 0px 16px 0px rgba(0, 0, 0, 0.2);
}

.boggle-cell:hover {
  transform: rotateX(10deg) rotateY(-10deg) translateZ(10px) scale(1.05);
  box-shadow: 0px 6px 12px rgba(0, 0, 0, 0.16), 0px 6px 12px rgba(0, 0, 0, 0.23);
}

.boggle-cell.active {
  background-color: #ffd700;
  color: #ffffff;
  transform: rotateX(10deg) rotateY(-10deg) translateZ(10px) scale(1.05);
  box-shadow: 0px 6px 12px rgba(0, 0, 0, 0.16), 0px 6px 12px rgba(0, 0, 0, 0.23);
}

/* Example Usage */
.boggle-board {
  width: 400px;
  height: 400px;
}

.boggle-cell {
  width: 80px;
  height: 80px;
}

@keyframes shuffle{
   0%{
    transform: rotateX(10deg) rotateY(-10deg) translateZ(10px) scale(1.05);
    box-shadow: 0px 6px 12px rgba(0, 0, 0, 0.16), 0px 6px 12px rgba(0, 0, 0, 0.23);
   }
   100%{
    box-shadow: 0px 0px 16px 0px rgba(0, 0, 0, 0.2);
   } 
}

.refreshArea {
  margin-top: 10px;
  /* width: 100vw; */
  display: flex;
  justify-content: center;
}
</style>