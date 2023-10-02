<template>
  <div class="boggleItems refresh" @click="renderDice">REFRESH BOARD</div>

  <!-- <div class="boggleItems popUp" :class="{hidden: !popUpStatus}">
    Are you sure?
    <div class="confirm popUpButtons">
        Confirm
    </div>
    <div class="no popUpButtons">
        No
    </div>
  </div> -->
</template>

<script>
export default {
  name: "RefreshButton",
  data() {
    return {
      letters: [],
      letterCount: {
        a: 23,
        b: 1,
        c: 4,
        d: 7,
        e: 26,
        f: 8,
        g: 5,
        h: 7,
        i: 12,
        j: 1,
        k: 1,
        l: 7,
        m: 5,
        n: 15,
        o: 13,
        p: 5,
        q: 2,
        r: 13,
        s: 9,
        t: 15,
        u: 9,
        v: 2,
        w: 3,
        x: 1,
        y: 6,
        z: 2,
      },
    };
  },
  methods: {
    createArray() {
      const letterObj = this.letterCount;
      for (const times in letterObj) {
        const repeatedLetters = times.repeat(letterObj[times]);
        for (const char of repeatedLetters) {
          this.letters.push(char);
        }
      }
    },

    randomNumber() {
      return Math.floor(Math.random() * this.letters.length);
    },

    renderDice() {
      const randomNum = this.randomNumber();
      return "boggleCell" ,this.letters[randomNum]
    },
  },
  
  mounted() {
    this.createArray();
  },
};
</script>

<style>
.refresh {
  display: flex;
  align-items: center;
  justify-content: center;
  font-size: 25px;
  cursor: pointer;
  width: 350px;
  height: 75px;
  background: #42b883;
  font-weight: bold;
  transition: all 0.4s ease;
}

.refresh:hover {
  background: #318a62;
  transform: scale(1.05);
}

.popUp {
  position: absolute;
  top: 45%;
  left: 40%;
  padding: 1.5rem;
}

.popUpButtons {
  border-radius: 6px;
}

.hidden {
  visibility: hidden;
}
</style>