<script setup>
import { onMounted, reactive, ref, computed } from "vue";
import ListPokemons from "../components/ListPokemons.vue";
import CardPokemonSelected from "@/components/CardPokemonSelected.vue";

let urlBaseSvg = ref(
  "https://raw.githubusercontent.com/PokeAPI/sprites/master/sprites/pokemon/other/dream-world/"
);
let pokemons = reactive(ref());
let searchPokemonField = ref("");
let pokemonSelected = reactive(ref());

onMounted(() => {
  fetch("https://pokeapi.co/api/v2/pokemon?limit=151&offset=0")
    .then((res) => res.json())
    .then((res) => (pokemons.value = res.results));
});

const pokemonsFiltered = computed(() => {
  if (pokemons.value && searchPokemonField.value) {
    return pokemons.value.filter((pokemon) =>
      pokemon.name
        .toLowerCase()
        .includes(searchPokemonField.value.toLowerCase())
    );
  }
  return pokemons.value;
});

const selectPokemon = (pokemon) => {
  fetch(pokemon.url)
    // o then significada quando eu tiver o retorno do json
    .then((res) => res.json())
    // entao  vou guardar ela numa variavel pokemonSelected
    .then((res) => (pokemonSelected.value = res));
  console.log(pokemonSelected.value);
};
</script>
<template>
  <main>
    <div class="container">
      <div class="row mt-6">
        <!-- Coluna para o componente CardPokemonSelected -->
        <div class="col-sm-12 col-md-6" style="margin-top: 80px">
          <CardPokemonSelected
            :name="pokemonSelected?.name"
            :xp="pokemonSelected?.base_experience"
            :height="pokemonSelected?.height"
            :image="pokemonSelected?.sprites.other.dream_world.front_default"
          />
        </div>

        <!-- Coluna para o restante do conteúdo -->
        <div class="col-sm-12 col-md-6 mt-4">
          <div class="card-list"></div>
          <div class="mb-3">
            <label hidden for="searchPokemonField" class="form-label"
              >Pokemon</label
            >
            <input
              v-model="searchPokemonField"
              type="text"
              class="form-control"
              id="searchPokemonField"
              placeholder="Pesquisar"
            />
          </div>

          <div class="card card-list bg-secondary">
            <div class="card-body row">
              <ListPokemons
                v-for="pokemon in pokemonsFiltered"
                :key="pokemon.name"
                :name="pokemon.name"
                :urlBaseSvg="urlBaseSvg + pokemon.url.split('/')[6] + '.svg'"
                @click="selectPokemon(pokemon)"
              />
            </div>
          </div>
        </div>
      </div>
    </div>
  </main>
</template>
<style scoped>
.card-list {
  max-height: 720px;
  overflow-y: scroll;
  overflow-x: hidden;
}
</style>
