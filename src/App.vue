<template>
  <div id="app">
    <main>
      <rules-component v-show="isNoob" @toggleOff="toggleRules" />

      <div class="game_data">
        <div class="options">
          <img src="./assets/images/logo.svg" alt="" />
        </div>
        <div class="score">
          <h4>SCORE</h4>
          <h2 class="counter">{{ this.point }}</h2>
        </div>
      </div>
      <!-- ./HEADER -->

      <Choice v-if="!hasPicked" @picked="pickedHand" />
      <!-- ./Choice -->

      <Matchup-component
        v-else
        :hand="this.hand"
        :counter="this.counter"
        :winner="this.winner"
        @playAgain="playAgain"
      />

      <div class="modal"></div>
    </main>

    <Footer @toggle="toggleRules" />
  </div>
</template>

<script>
import Choice from "./components/choice.vue";
import Footer from "./components/footer.vue";
import MatchupComponent from "./components/matchupComponent.vue";
import RulesComponent from "./components/rulesComponent.vue";

export default {
  data() {
    return {
      hasPicked: false,
      hand: "",
      counter: "",
      point: 0,
      winner: "",
      isNoob: false,
    };
  },
  components: {
    Choice,
    Footer,
    MatchupComponent,
    RulesComponent,
  },
  methods: {
    pickedHand(text) {
      this.hasPicked = true;
      this.hand = text;
      this.counter = Math.floor(Math.random() * 3);
      this.determineWinner();
    },

    playAgain() {
      this.hasPicked = false;
    },

    determineWinner() {
      setTimeout(() => {
        if (this.hand == "paper") {
          console.log();
          if (this.counter == 0) {
            this.winner = "tie";
          } else if (this.counter == 1) {
            this.winner = "pc";
            this.point -= 1;
            this.persist();
          } else {
            this.winner = "player";
            this.point += 1;
            this.persist();
          }
        } else if (this.hand == "scissors") {
          if (this.counter == 1) {
            this.winner = "tie";
          } else if (this.counter == 2) {
            this.winner = "pc";
            this.point -= 1;
            this.persist();
          } else {
            this.winner = "player";
            this.point += 1;
            this.persist();
          }
        } else {
          if (this.counter == 2) {
            this.winner = "tie";
          } else if (this.counter == 0) {
            this.winner = "pc";
            this.point -= 1;
            this.persist();
          } else {
            this.winner = "player";
            this.point += 1;
            this.persist();
          }
        }
      }, 2500);
    },

    toggleRules() {
      if (this.isNoob == false) {
        this.isNoob = true;
      } else {
        this.isNoob = false;
      }
    },

    persist() {
      localStorage.point = this.point;
    },
  },
  mounted() {
    if (localStorage.getItem("point")) {
      // this.point = localStorage.point;
      localStorage.removeItem(this.point);
    }
  },
};
</script>

<style lang="scss">
@import "./assets/style/common.scss";
@import url("https://fonts.googleapis.com/css2?family=Barlow+Semi+Condensed:wght@600;700&display=swap");

#app {
  min-height: 100vh;
  background: radial-gradient(hsl(214, 47%, 23%), hsl(237, 49%, 15%));
}

main {
  margin: auto;
  max-width: 1366px;
  // width: 1366px;
  padding-top: 3rem;

  .game_data {
    width: 50%;
    margin: auto;
    display: flex;
    border: 2px solid hsl(217, 16%, 45%);
    border-radius: 10px;
    padding: 1rem;
    justify-content: space-between;

    .options {
      line-height: 1.6rem;
      h1 {
        color: white;
      }
    }

    .score {
      height: 99px;
      width: 110.5px;
      text-align: center;
      line-height: 2rem;
      background-color: rgb(228, 228, 228);
      color: hsl(229, 64%, 46%);
      border-radius: 10px;

      h4 {
        padding-top: 0.5rem;
      }

      .counter {
        font-size: 3.5rem;
        color: hsl(229, 25%, 31%);
      }
    }
  }
}
</style>
