<template>
  <div class="cell" >
    {{ randomLetter }}
  </div>
</template>
  
  <script>
export default {
  name: "BoggleCell",
  props:{
    usedDice: Set,
    diceList: Array
  },
  methods: {
    randomNumber() {
              console.log(`size of usedDice: ${this.usedDice.size} size of dice-list: ${this.diceList.length}`);
              if (this.diceList.length <= 0 || this.usedDice.size === 16) {
                return null
              } 
              let randomDice;
              do {
                randomDice = Math.floor(Math.random() * 16);
                console.log(`current random is :${randomDice}, is it already used: ${this.usedDice.has(randomDice)}`);
              } while (this.usedDice.has(randomDice))
              this.$emit("minimizeDice", randomDice)
              console.log("final random is:" + " " + this.diceList[randomDice]);
              return randomDice
          },

    randomNumberSmall() {
      return Math.floor(Math.random() * 6);
    },
},
computed:{
    randomLetter() {  
      const randomNum = this.randomNumber();
      const randomNumSM = this.randomNumberSmall();
      console.log("currentDice }}}}}" + " " + this.diceList[randomNum]);
      console.log("randoms" + " " + randomNum);
      return this.diceList.length >= 0 ? this.diceList[randomNum][randomNumSM] : null;
    }
  }
};
</script>