<template>
  <div :class="todo.statut">
    <h1>{{ todo.nom }}</h1>
    <p>{{ todo.desc }}</p>
    <p class="btn">
      <button v-show="todo.statut=='waiting'" @click="start">Start</button>
      <button v-show="todo.statut=='started'" @click="end">End</button>
      <button @click="del">Delete</button>
  </p>
  </div>
</template>

<script>
  export default {
    name: 'MyTodo',
    props: {
      todo: Object
    },
    methods: {
      start() {
        this.$emit('start', this.todo.id);
      },
      end() {
        this.$emit('end', this.todo.id);
      },
      del() {
        this.$emit('del', this.todo.id);
      }
    }
  }
</script>

<style scoped>
.waiting {
  background: limegreen;
}
.started {
  background: orange;
}
.ended {
  background: crimson;
}
p.btn {
  text-align:center;
}
</style>