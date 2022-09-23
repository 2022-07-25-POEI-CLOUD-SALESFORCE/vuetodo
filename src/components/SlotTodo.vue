<template>
  <div class="total">
    <slot></slot> Tâches
  </div>
</template>

<script>
  // un slot sert uniquement à l'affichage (réutilisation)
  export default {
    name: 'SlotTodo'
  }
</script>

<style scoped>
  .total {
    color: black;
    margin: 1.5em 2px;
    font-size: 4em;
    text-shadow: 3px 3px 3px silver;
    text-align: center;
  }
</style>