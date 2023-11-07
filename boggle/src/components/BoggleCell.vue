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
              let randomDice;
              do {
                randomDice = Math.floor(Math.random() * 26);
              } while (this.usedDice.has(randomDice));  
              this.$emit("minimizeDice", randomDice)
              return randomDice
          },

    randomNumberSmall() {
      return Math.floor(Math.random() * 6);
    },
},
computed:{
    randomLetter() {  
      const randomNum = this.randomNumber()
      const randomNumSM = this.randomNumberSmall();
      console.log("randoms" + " " + this.diceList[randomNum]);
      // if (this.diceList.length > 0) {
      //   const currentDice = this.diceList[randomNum];
      //   // this.diceList.splice(randomNum, 1)
      //   return currentDice[randomNumSM]
      // } else {
      //   return null;
      // }
      return this.diceList.length > 0 ? this.diceList[randomNum][randomNumSM] : null;
    }
  }
};
</script>