<template>
  <div id="app">
    <img alt="Vue logo" src="./assets/logo.png">
    <AppHeader :total="todoData.length" v-bind:todo="todoData.length-countDone()" v-bind:done="countDone()" />
    <TodoList :todos=todoData v-on:removeItem="removeItem" v-on:doneItem="toggleDoneItem" />
    <ItemAddForm v-on:labelText="addItem($event)" />
  </div>
</template>

<script>
import AppHeader from './components/AppHeader.vue'
import TodoList from './components/TodoList.vue'
import ItemAddForm from './components/ItemAddForm.vue'

var idx = 0;

export default {
  name: 'app',
  components: {
    AppHeader,
    TodoList,
    ItemAddForm
  },
  data() {
    return {
      todoData: [
        this.createTodoItem('Drink Coffe'),
        this.createTodoItem('Code'),
        this.createTodoItem('Make App')
      ]
    }
  },
  methods: {
    createTodoItem: function(label) {
      return {
        label: label,
        done: false,
        id: idx++
      }
    },
    addItem: function(item) {
      this.todoData.push(this.createTodoItem(item));
    },
    removeItem: function(id) {
      const idx = this.todoData.findIndex((el) => el.id === id);
      this.todoData.splice(idx, 1);
    },
    toggleDoneItem: function(id) {
      const idx = this.todoData.findIndex((el) => el.id === id);
      const el = this.todoData[idx];
      el.done = !el.done;
    },
    countDone: function() {
      var done = this.todoData.filter((el) => el.done);
      return done.length;
    }
  }
}
</script>

<style>

* {
  box-sizing: border-box;
}

#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin: 60px auto 0 auto;
  max-width: 600px;
}

ul {
  margin: 0;
  padding: 0;
}

li {
  list-style: none;
  margin: 0;
  padding: 0;
  text-align: left;
}
</style>
