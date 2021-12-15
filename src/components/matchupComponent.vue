<template>
  <div class="matchup">
    <div class="player_choice">
      <h2 class="pick">YOU PICKED</h2>
      <div class="choice" :class="this.hand">
        <img :src="require(`../assets/images/icon-${this.hand}.svg`)" alt="" />
      </div>
    </div>

    <transition name="fade">
      <div class="result" v-show="haveWinner">
        <h2>{{ this.whoWon }}</h2>
        <button @click="$emit('playAgain')">PLAY AGAIN</button>
      </div>
    </transition>
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
    winner: String,
  },
  data() {
    return {
      options: ["paper", "scissors", "rock"],
      haveWinner: false,
    };
  },
  mounted() {
    setTimeout(() => (this.haveWinner = true), 2500);
  },
  computed: {
    whoWon() {
      if (this.winner == "player") {
        return "YOU WIN";
      } else if (this.winner == "pc") {
        return "YOU LOSE";
      } else {
        return "ITS A TIE";
      }
    },
  },
};
</script>

<style lang="scss">
.matchup {
  width: 45%;
  margin: auto;
  display: flex;
  margin-bottom: 4rem;
  justify-content: space-between;
  align-items: center;
  height: 350px;
  margin-top: 6rem;
  animation-name: slide;
  animation-delay: 1s;
  animation-duration: 2s;
  animation-fill-mode: forwards;

  .fade-enter-active,
  .fade-leave-active {
    transition: opacity 0.5s ease;
  }

  .fade-enter-from,
  .fade-leave-to {
    opacity: 0;
  }

  @keyframes slide {
    from {
      width: 45%;
    }
    to {
      width: 80%;
    }
  }

  .pick {
    color: white;
    font-size: 600;
    padding-bottom: 4rem;
  }

  .choice {
    display: flex;
    justify-content: center;
    align-items: center;
    width: 250px;
    height: 250px;
    border-radius: 50%;
    border: 25px solid transparent;
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

  .result {
    h2 {
      color: white;
      font-size: 4rem;
      margin-bottom: 1rem;
    }

    button {
      color: hsl(349, 70%, 56%);
      width: 100%;
      height: 3rem;
      border-radius: 10px;
      background-color: white;
      font-size: 1.2rem;
      letter-spacing: 2.5px;

      &:hover {
        cursor: pointer;
      }
    }
  }
}
</style>