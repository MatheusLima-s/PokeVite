<script setup>
const pokemon = defineProps(["name", "xp", "height", "image"]);
</script>

<template>
  <div
    class="card bg-dark"
    style="border: 1px solid rgba(177, 176, 176, 0.671)"
  >
    <img
      v-if="pokemon.name"
      :src="pokemon.image"
      class="card-img-top pt-2"
      :alt="pokemon.name"
      height="250"
    />
    <img
      v-else
      src="../assets/egg_pokemon.svg"
      class="card-img-top pt-2"
      :alt="pokemon.name"
      height="250"
    />
    <h5 class="card-title text-center">{{ pokemon.name }}</h5>
    <hr />
    <div v-if="pokemon.name" class="row p-3">
      <section class="col">
        <!-- Adiciona margem na parte superior -->
        <strong>XP: </strong>
        <span>{{ pokemon.xp }} %</span>
      </section>
      <section class="col">
        <!-- Adiciona margem na parte superior -->
        <strong>Altura: </strong>
        <span>{{ pokemon.height }}</span>
      </section>
    </div>
    <div v-else class="row p-3">
      <section class="col">
        <!-- Adiciona margem na parte superior -->
      </section>
      <section class="col">
        <!-- Adiciona margem na parte superior -->
      </section>
    </div>
  </div>
</template>

<style scoped>
card {
  --bs-bg-opacity: 1;
  /* Definindo a cor branca diretamente */
  --bs-secondary-rgb: 255, 255, 255; /* Cor branca */
  background-color: rgba(
    var(--bs-secondary-rgb),
    var(--bs-bg-opacity)
  ) !important;
}
h5,
hr,
strong,
span {
  color: white;
}
</style>
