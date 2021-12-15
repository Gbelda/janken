<template>
  <div id="app">
    <main>
      <div class="game_data">
        <div class="options">
          <img src="./assets/images/logo.svg" alt="" />
        </div>
        <div class="score">
          <h4>SCORE</h4>
          <h2 class="counter">12</h2>
        </div>
      </div>
      <!-- ./HEADER -->

      <Choice v-if="!hasPicked" @picked="pickedHand" />
      <!-- ./Choice -->

      <Matchup-component v-else :hand="this.hand" :counter="this.counter" />

      <div class="modal"></div>
    </main>

    <Footer />
  </div>
</template>

<script>
import Choice from "./components/choice.vue";
import Footer from "./components/footer.vue";
import MatchupComponent from "./components/matchupComponent.vue";

export default {
  data() {
    return {
      hasPicked: false,
      hand: "",
      counter: "",
    };
  },
  components: {
    Choice,
    Footer,
    MatchupComponent,
  },
  methods: {
    pickedHand(text) {
      this.hasPicked = true;
      this.hand = text;
      this.counter = Math.floor(Math.random() * 3);
    },
  },
};
</script>

<style lang="scss">
@import "./assets/style/common.scss";
@import url("https://fonts.googleapis.com/css2?family=Barlow+Semi+Condensed:wght@600;700&display=swap");

#app {
  background: radial-gradient(hsl(214, 47%, 23%), hsl(237, 49%, 15%));
  min-height: 100vh;
}

main {
  margin: auto;
  max-width: 1366px;
  min-width: 1366px;
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
