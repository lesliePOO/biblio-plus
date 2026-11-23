<template>
  <footer class="app-footer">
    <p class="app-footer__name">Biblio+ — Bibliothèque municipale</p>
    <p>Ouvert du mardi au samedi</p>
    <p><RouterLink to="/contact">Nous contacter</RouterLink></p>
  </footer>
</template>

<style scoped>
.app-footer {
  margin-top: var(--space-6);
  padding: var(--space-4) var(--space-6);
  background: var(--color-text);
  color: var(--color-surface);
}

.app-footer p {
  margin: 0;
}

.app-footer__name {
  font-weight: 700;
}

.app-footer a {
  color: inherit;
}

.app-footer a:focus-visible {
  outline-color: var(--color-surface);
}
</style>
