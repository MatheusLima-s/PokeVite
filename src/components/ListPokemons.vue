<script setup>
const pokemon = defineProps(["name", "urlBaseSvg"]);
</script>
<template>
  <div class="col-4 col-md-6 col-xl-3">
    <div class="card p-2 mb-3 cardListPokemon bg-dark">
      <p class="text-center">{{ pokemon.name }}</p>
      <img :src="urlBaseSvg" class="card-img-top" alt="..." height="80" />
    </div>
  </div>
</template>
<style scoped>
p {
  color: white;
}

.cardListPokemon:hover p {
  color: black; /* Alterando a cor do texto para preto ao passar o mouse sobre .cardListPokemon */
}

.cardListPokemon {
  cursor: pointer;
}

.cardListPokemon:hover {
  --bs-bg-opacity: 1;
  /* Definindo a cor branca diretamente */
  --bs-secondary-rgb: 255, 255, 255; /* Cor branca */
  background-color: rgba(
    var(--bs-secondary-rgb),
    var(--bs-bg-opacity)
  ) !important;
}

.cardListPokemon img:hover {
  padding: 0.1rem;
}
</style>
