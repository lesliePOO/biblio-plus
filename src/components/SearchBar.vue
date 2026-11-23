<script setup>
const model = defineModel({ type: String, default: '' })
</script>

<template>
  <form class="search" role="search" @submit.prevent>
    <label for="q" class="sr-only">Rechercher un livre</label>
    <input id="q" v-model="model" class="search__input" type="search" placeholder="Titre, auteur…" />
  </form>
</template>

<style scoped>
.search__input {
  width: 100%;
  max-width: 28rem;
  padding: var(--space-2) var(--space-4);
  border: 2px solid var(--color-border);
  border-radius: var(--radius);
  font: inherit;
}
</style>
