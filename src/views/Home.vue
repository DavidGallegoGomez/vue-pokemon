<template>
  <div class="home">
    <div class="actions-container">
      <button @click="fight">FIGHT</button>
    </div>

    <div :class="['box', { winner: player1.winner }]">
      <select v-model="player1.pokemon" @change="resetWinner">
        <option
          v-for="pokemon in pokemons"
          :value="pokemon"
          :key="pokemon.id"
          >{{ pokemon.name.toUpperCase() }}</option
        >
      </select>
      <pokemon :class="player1.pokemon.name"></pokemon>
    </div>

    <label>VS</label>

    <div :class="['box', { winner: player2.winner }]">
      <select v-model="player2.pokemon" @change="resetWinner">
        <option
          v-for="pokemon in pokemons"
          :value="pokemon"
          :key="pokemon.id"
          >{{ pokemon.name.toUpperCase() }}</option
        >
      </select>
      <pokemon :class="player2.pokemon.name"></pokemon>
    </div>
  </div>
</template>

<script>
// @ is an alias to /src
import Pokemon from "@/components/Pokemon.vue";

export default {
  name: "home",
  components: {
    Pokemon
  },
  data: () => ({
    player1: { pokemon: {}, winner: false },
    player2: { pokemon: {}, winner: false },
    pokemons: [
      { id: 0, name: "picachu", type: "electro" },
      { id: 1, name: "bulbasaur", type: "planta" },
      { id: 2, name: "squirtle", type: "agua" },
      { id: 3, name: "charmander", type: "fuego" }
    ],
    results: [
      [0, 2, 1, 0],
      [1, 0, 2, 2],
      [2, 1, 0, 1],
      [0, 1, 2, 0]
    ]
  }),
  methods: {
    fight: function() {
      const result = this.results[this.player1.pokemon.id][
        this.player2.pokemon.id
      ];
      const selectWinner = [
        () => {
          (this.player1.winner = true), (this.player2.winner = true);
        }, // empate
        () => {
          (this.player1.winner = true), (this.player2.winner = false);
        }, // gana player1
        () => {
          (this.player1.winner = false), (this.player2.winner = true);
        } // gana player2
      ];
      selectWinner[result]();
    },
    resetWinner: function() {
      (this.player1.winner = false), (this.player2.winner = false);
    }
  }
};
</script>

<style scoped lang="scss">
.box {
  display: inline-block;
  padding: 1rem;
  margin: 1rem;
}
.box.winner {
  @extend .box;
  background-color: green;
}
</style>
