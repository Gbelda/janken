<template>
  <div class="matchup">
    <div class="player_choice">
      <h2 class="pick">YOU PICKED</h2>
      <div class="choice" :class="this.hand">
        <img :src="require(`../assets/images/icon-${this.hand}.svg`)" alt="" />
      </div>
    </div>
    <div class="pc_choice">
      <h2 class="pick">THE HOUSE PICKED</h2>
      <div class="choice" :class="this.options[counter]">
        <img
          :src="require(`../assets/images/icon-${this.options[counter]}.svg`)"
          alt=""
        />
      </div>
    </div>
  </div>
</template>

<script>
export default {
  props: {
    hand: String,
    counter: Number,
  },
  data() {
    return {
      options: ["paper", "scissors", "rock"],
    };
  },
};
</script>

<style lang="scss">
.matchup {
  width: 60%;
  margin: auto;
  display: flex;
  margin-bottom: 4rem;
  justify-content: space-between;
  height: 350px;
  margin-top: 6rem;

  .pick {
    color: white;
    font-size: 600;
    padding-bottom: 4rem;
  }

  .choice {
    display: flex;
    justify-content: center;
    align-items: center;
    width: 200px;
    height: 200px;
    border-radius: 50%;
    border: 15px solid transparent;
  }

  .paper {
    background: linear-gradient(rgb(255, 255, 255), rgb(255, 255, 255))
        padding-box,
      linear-gradient(to right, hsl(230, 89%, 62%), hsl(230, 89%, 65%))
        border-box;
  }

  .scissors {
    background: linear-gradient(rgb(255, 255, 255), rgb(255, 255, 255))
        padding-box,
      linear-gradient(to right, hsl(39, 89%, 49%), hsl(40, 84%, 53%)) border-box;
  }

  .rock {
    background: linear-gradient(rgb(255, 255, 255), rgb(255, 255, 255))
        padding-box,
      linear-gradient(to right, hsl(349, 71%, 52%), hsl(349, 70%, 56%))
        border-box;
  }
}
</style>