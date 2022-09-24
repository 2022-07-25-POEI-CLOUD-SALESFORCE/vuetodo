<template>
  <!-- le statut est passé comme classe CSS pour personnaliser l'affichage -->
    <div class="myTodo" :class="todo.statut">
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
        //émission d'events vers le parent avec l'id à traiter
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
  .myTodo {
    padding: 5px;
    margin: 5px;
    text-align: center; 
  }
  h1{
    font-size: 3em;
    text-shadow: 5px 5px 5px rgba(0, 0, 0, .6);
  }
  p {
    font-size: 1.2em;
  }
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
button {
  border-color: white;
  background: black;
  color: white;
  padding: 10px;
  margin: 2px;
}
</style>