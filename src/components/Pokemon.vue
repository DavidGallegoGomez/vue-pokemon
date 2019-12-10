<template>
  <div class="pokemon">
    <div class="pokemon-head"></div>
    <div class="pokemon-body"></div>
    <div class="pokemon-feet"></div>
  </div>
</template>

<script>
export default {
  name: "Pokemon"
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped lang="scss">
.pokemon {
  width: 3rem;
  display: inline-block;
  margin: 1rem;
}
.pokemon-head,
.pokemon-body {
  height: 3rem;
}
.pokemon-feet {
  height: 1rem;
}

.pokemon.bulbasaur .pokemon-head {
  background-color: #ff6a62;
}
.pokemon.bulbasaur .pokemon-body {
  background-color: #62d5b4;
}
.pokemon.bulbasaur .pokemon-feet {
  background-color: #317373;
}

.pokemon.squirtle .pokemon-head,
.pokemon.squirtle .pokemon-body {
  background-color: #8bc5cd;
}
.pokemon.squirtle .pokemon-feet {
  background-color: #ffe69c;
}

.pokemon.charmander {
  background-color: #de5239;
}

.pokemon.picachu {
  background-color: #f6e652;
}
</style>
