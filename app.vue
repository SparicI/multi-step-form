<template>
  <main>
    <div class="multi-step-form-container">
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
    place-items: center;
  }

  .multi-step-form-container {
    background-color: red;
    padding: 1rem;
    border-radius: 10px;
    height: 70vh;
    max-width: 940px;
  }

}
</style>
