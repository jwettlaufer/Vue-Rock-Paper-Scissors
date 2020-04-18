<template>
  <section id="rps">
    <h2 id="text">Rock Paper Scissors</h2>
    <p>
      Player
      <i class="fa fa-5x fa-fw" :class="computedPlayer"></i>
      <i class="fa fa-5x fa-fw" :class="computedRand"></i>
      Computer
    </p>
    <div>
      <button @click="choose('rock')">
        <i class="fa fa-hand-rock-o fa-2x"></i>
      </button>

      <button @click="choose('paper')">
        <i class="fa fa-hand-paper-o fa-2x"></i>
      </button>
      <button @click="choose('scissors')">
        <i class="fa fa-hand-scissors-o fa-2x"></i>
      </button>
    </div>
    <p>{{ playerScore }} - {{ computerScore }}</p>
  </section>
</template>
 
<script>
export default {
  name: "Rps",
  data() {
    return {
      playerPick: null,
      randPick: null,
      playerScore: 0,
      computerScore: 0
    };
  },
  methods: {
    choose(pick) {
      this.playerPick = pick;
      const picks = ["rock", "paper", "scissors"];
      this.randPick = picks[Math.floor(Math.random() * picks.length)];
      this.setScore();
    },
    setScore() {
      if (this.playerPick === this.randPick) {
        console.log("Draw");
        return "Draw, try again!";
      }
      if (this.playerPick === "rock") {
        if (this.randPick === "paper") {
          this.computerScore++;
          console.log("Computer wins");
          return 'Computer wins!';
        } else if (this.randPick == "scissors") {
          console.log("Player wins");
          this.playerScore++;
          return "Player wins!";
        }
      } else if (this.playerPick === "paper") {
        if (this.randPick === "rock") {
          console.log("Player wins");
          this.playerScore++;
          return "Player wins!";
        } else if (this.randPick === "scissors") {
          console.log("Computer wins");
          this.computerScore++;
          return 'Computer wins!';
        }
      } else {
        if (this.randPick === "rock") {
          console.log("Computer wins");
          this.computerScore++;
          return 'Computer wins!';
        } else if (this.randPick === "paper") {
          console.log("Player wins");
          this.playerScore++;
          return "Player wins!";
        }
      }
    }
  },
  computed: {
    computedPlayer() {
      return {
        "fa fa-spinner fa-pulse": this.playerPick === null,
        "fa-hand-rock-o": this.playerPick === "rock",
        "fa-hand-paper-o": this.playerPick === "paper",
        "fa-hand-scissors-o": this.playerPick === "scissors"
      };
    },
    computedRand() {
      return {
        "fa fa-spinner fa-pulse": this.randPick === null,
        "fa-hand-rock-o": this.randPick === "rock",
        "fa-hand-paper-o": this.randPick === "paper",
        "fa-hand-scissors-o": this.randPick === "scissors"
      };
    }
  }
};
</script>

<style>
#rps {
  height: 90vh;
  display: flex;
  flex-direction: column;
  justify-content: center;
  margin: 0 auto;
  color: white;
}
h2 {
    font-size: 40px;
    text-transform: uppercase;
}
p {
  font-size: 30px;
  font-weight: bold;
}
</style>