<template>
  <div class="cell" @click="randomNumberSmall">
    {{ randomLetter() }}
  </div>
</template>
  
  <script>
export default {
  name: "RefreshButton",
  data() {
    return {
      letter: "",
      letters: [],
      usedDice: [],
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
      console.log("array created!!!");
    },

    randomNumber() {
              let randomDice;
              do {
                  randomDice = Math.floor(Math.random() * this.letters.length);
                  console.log("hello isreal");
              } while (this.usedDice.includes(randomDice));

              this.usedDice.push(randomDice)
              return randomDice;
          },

    randomNumberSmall() {
      return Math.floor(Math.random() * 6);
    },

    randomLetter() {
      const randomDice = this.randomNumber()
      const randomNum = randomDice
      const randomNumSM = this.randomNumberSmall();
      if (this.letters.length > 0) {
        return this.letters[randomNum][randomNumSM];
      } else {
        return null;
      }
    },
  },
  computed: {
   
  },
  mounted() {
    this.createArray();
  },
};
</script>