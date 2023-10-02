<template>
  <div class="cell" @click="randomNumberSmall">
    {{ randomLetter }}
  </div>
</template>
  
  <script>
export default {
  name: "RefreshButton",
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
      this.letters = this.letters.length < 1 ? letterArray.split("\n").map((set) => set.split('')) : this.letters
      console.log(`what child is this? : ${this.letters[0][1]}`);
      console.log("array created!!!");
      
    },

    randomNumber() {
      return Math.floor(Math.random() * this.letters.length);
    },
    randomNumberSmall(){
        return Math.floor(Math.random() * 6);
        
    }
  },
  computed: {
    randomLetter() {
      const randomNum = this.randomNumber()
      const randomNumSM = this.randomNumberSmall()
      if(this.letters.length > 0 ){
        return this.letters[randomNum][randomNumSM]
      } else{
        return null
      }
      
    },
  },
  mounted() {
    this.createArray();
  },
};
</script>