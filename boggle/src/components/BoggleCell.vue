<template>
  <div class="cell" >
    {{ randomLetter }}
  </div>
</template>
  
  <script>
export default {
  name: "RefreshButton",
  props:{
    usedDice: Array,
  },
  data() {
    return {
      letter: "",
      letters: [],
      lettersList: `aaafrs
aaeeee
aafirs
adennn
aeeeem
aeegmu
aegmnn
afirsy
bjkqxz
ccenst
ceiilt
ceilpt
ceipst
ddhnot
dhhlor
dhlnor
dhlnor
eiiitt
emottt
ensssu
fiprsy
gorrvw
iprrry
nootuw
ooottu`,
    };
  },
  methods: {
    createArray() {
      const letterArray = this.lettersList;
      this.letters = this.letters.length < 1 ? letterArray.split("\n").map((set) => set.split("")) : this.letters;
    },

    randomNumber() {
        console.log("next loop:");
              let randomDice;
              do {
                  randomDice = Math.floor(Math.random() * this.letters.length);
              } while (this.usedDice.includes(randomDice));
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
      console.log("randomNumber :::", randomNum);
      const randomNumSM = this.randomNumberSmall();
      if (this.letters.length > 0) {
        const currentDice = this.letters[randomNum];
        // this.letters.splice(randomNum, 1)
        return currentDice[randomNumSM]
      } else {
        return null;
      }
    }
  },
  mounted() {
    this.createArray();
  },
};
</script>