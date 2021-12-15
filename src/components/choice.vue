<template>
  <div class="select">
    <div class="paper" @click="$emit('picked', paper)">
      <img src="../assets/images/icon-paper.svg" alt="" />
    </div>
    <div class="scissors" @click="$emit('picked', scissors)">
      <img src="../assets/images/icon-scissors.svg" alt="" />
    </div>
    <div class="rock" @click="$emit('picked', rock)">
      <img src="../assets/images/icon-rock.svg" alt="" />
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      paper: "paper",
      scissors: "scissors",
      rock: "rock",
    };
  },
};
</script>

<style lang="scss">
.select {
  width: 45%;
  margin: auto;
  height: 350px;
  background-image: url("../assets/images/bg-triangle.svg");
  background-size: contain;
  background-repeat: no-repeat;
  background-position: center;
  margin-top: 10rem;
  position: relative;

  .paper {
    position: absolute;
    top: -25%;
    left: 10%;
    background: linear-gradient(rgb(255, 255, 255), rgb(255, 255, 255))
        padding-box,
      linear-gradient(to right, hsl(230, 89%, 62%), hsl(230, 89%, 65%))
        border-box;
  }

  .scissors {
    position: absolute;
    top: -25%;
    right: 10%;
    background: linear-gradient(rgb(255, 255, 255), rgb(255, 255, 255))
        padding-box,
      linear-gradient(to right, hsl(39, 89%, 49%), hsl(40, 84%, 53%)) border-box;
  }

  .rock {
    position: absolute;
    bottom: -10%;
    left: 35%;
    background: linear-gradient(rgb(255, 255, 255), rgb(255, 255, 255))
        padding-box,
      linear-gradient(to right, hsl(349, 71%, 52%), hsl(349, 70%, 56%))
        border-box;
  }
}
</style>