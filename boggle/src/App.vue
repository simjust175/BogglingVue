<template>
  <img
    alt="Vue logo"
    class="logo"
    src="./assets/logo.svg"
    width="125"
    height="125"
  />
  <div class="mainContainer">
    <div class="boggle-board boggleItems">
      <BoggleCell
        @boggleCellCreater="boggleCellCreater"
        class="boggle-cell"
        v-for="(cell, index) in 16"
        :key="index"
      />
    </div>
    <div class="timerArea">
      <BoggleTimer :timer-state="timerOn()" />
    </div>
  </div>
  <div class="refreshArea">
  <div class="refresh">
    <RefreshButton />
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
  methods: {
    boggleCellCreater(letter) {
      console.log(`this is the $emit: ${letter}`);
    },
    timerOn() {
      return "timerProgress";
    },
  },
};
</script>

<style>
:root {
  --color-primary: #42b883;
  --color-secondary-dark: #388f68;
  --border-radius: 8px;
}
.boggleItems {
  border-radius: var(--border-radius);
  border: 1px #42b883 solid;
}

.mainContainer {
  display: flex;
  justify-content: space-around;
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

.refreshArea{
  margin-top: 10px;
  width: 100vw;
  display: flex;
  justify-content: center;
}
</style>