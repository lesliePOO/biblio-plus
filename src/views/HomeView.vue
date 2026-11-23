<script setup>
import { ref, computed, onMounted } from 'vue'
import SearchBar from '@/components/SearchBar.vue'
import BookList from '@/components/BookList.vue'
import { useBooks } from '@/composables/useBooks'

const { books, loading, error, load } = useBooks()
const query = ref('')
const featured = computed(() =>
  books.value.filter((b) => b.title.toLowerCase().includes(query.value.toLowerCase())).slice(0, 8),
)

onMounted(load)
</script>

<template>
  <section class="hero">
    <h1>Bienvenue à la bibliothèque</h1>
    <SearchBar v-model="query" />
  </section>

  <section class="featured" aria-labelledby="coeur">
    <h2 id="coeur">Coups de cœur</h2>
    <p v-if="loading" role="status">Chargement…</p>
    <p v-else-if="error" role="alert">{{ error }}</p>
    <BookList v-else :books="featured" />
  </section>
</template>

<style scoped>
.hero,
.featured {
  padding: var(--space-6);
}

.hero h1 {
  margin-top: 0;
  font-size: var(--fs-600);
}
</style>
