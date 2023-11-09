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
      lettersList: `aaciot
abilty
abjmo1
acdemp
acelrs
adenvz
ahmors
biforx
denosw
dknotu
eefhiy
egkluy
egintv
ehinps
elpstu
gilruw`,
    }
  },
  methods: {

    createArray() {
      const letterArray = this.lettersList;
      this.letters = letterArray.split("\n").map((set) => set.split(""));
      console.log("new array created !!!");
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

.refresh:active {
  background: #318a62;
  transform: scale(0.9);
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