<script setup>
defineProps({
  book: { type: Object, required: true },
  favorite: { type: Boolean, default: false },
})
const emit = defineEmits(['toggle-favorite'])
</script>

<template>
  <article class="book-card">
    <img
      class="book-card__cover"
      :src="book.cover"
      width="200"
      height="300"
      :alt="'Couverture de ' + book.title"
      loading="lazy"
    />
    <div class="book-card__body">
      <h3 class="book-card__title">{{ book.title }}</h3>
      <p class="book-card__author">{{ book.author }}</p>
      <p class="book-card__status" :class="{ 'book-card__status--off': !book.available }">
        {{ book.available ? 'Disponible' : 'Emprunté' }}
      </p>
      <button
        class="book-card__fav"
        type="button"
        :aria-pressed="favorite"
        @click="emit('toggle-favorite', book.id)"
      >
        {{ favorite ? '★ Retirer des favoris' : '☆ Ajouter aux favoris' }}
      </button>
      <slot name="actions" />
    </div>
  </article>
</template>

<style scoped>
.book-card {
  background: var(--color-surface);
  border-radius: var(--radius);
  box-shadow: var(--shadow-card);
  overflow: hidden;
}

.book-card__cover {
  display: block;
  width: 100%;
  object-fit: cover;
  border-radius: var(--radius) var(--radius) 0 0;
}

.book-card__body {
  padding: var(--space-4);
}

.book-card__title {
  margin: 0;
  font-size: var(--fs-300);
}

.book-card__author {
  margin: var(--space-2) 0;
}

.book-card__status {
  margin: 0 0 var(--space-2);
  font-weight: 600;
}

.book-card__status--off {
  color: var(--color-danger);
}

.book-card__fav {
  padding: var(--space-2) var(--space-4);
  border: 2px solid var(--color-primary);
  border-radius: var(--radius);
  background: transparent;
  color: var(--color-primary);
  font: inherit;
  cursor: pointer;
}

.book-card__fav[aria-pressed='true'] {
  background: var(--color-primary);
  color: var(--color-primary-contrast);
}
</style>
