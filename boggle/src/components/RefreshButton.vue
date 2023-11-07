<template>
  <div class="boggleItems refresh" @click="createArray">REFRESH BOARD</div>

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
  name: "DiceCreater",
  data() {
    return {
      letters: [],
      lettersList: `000000
aaafrs
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
    }
  },
  methods: {

    createArray() {
      const letterArray = this.lettersList;
      this.letters = letterArray.split("\n").map((set) => set.split(""));
      this.$emit("createdList", this.letters)
    },
  },
  mounted() {
    this.createArray()
  }
}
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