<template>
  <main>
    <div class="multi-step-form-container">
      <h1 class="visually-hidden">Multi step form</h1>
      <TheStepIndicator />
      <TheForm />
    </div>
  </main>
</template>

<script
  setup
  lang="ts"
></script>

<style scoped>
@media screen and (min-width: 1024px) {
  main {
    display: grid;
    align-items: center;
  }

  .multi-step-form-container {
    display: flex;
    padding: var(--spacing-400);
    border-radius: var(--border-radius-soft);
    min-height: 70vh;
    max-width: 1024px;
    margin-inline: auto;
    background-color: var(--white);
  }

}
</style>
