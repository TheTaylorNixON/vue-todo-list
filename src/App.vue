<template>
  <div id="app">
    <img alt="Vue logo" src="./assets/logo.png">
    <AppHeader :total="todoData.length" v-bind:todo="todoData.length-countDone" v-bind:done="countDone" />
    <div class="top-panel d-flex">
      <SearchPanel @searchChange="searchChange($event)" />
      <ItemStatusFilter @statusFilter="filter=$event" :filter="filter" />
    </div>
    <TodoList :todos="visibleItems(todoData, term, filter)"
      @removeItem="removeItem"
      @doneItem="toggleDoneItem" 
      @importantItem="toggleImportantItem"
    />
    <ItemAddForm @labelText="addItem($event)" />
  </div>
</template>

<script>
import AppHeader from './components/AppHeader.vue'
import TodoList from './components/TodoList.vue'
import ItemAddForm from './components/ItemAddForm.vue'
import SearchPanel from './components/SearchPanel.vue'
import ItemStatusFilter from './components/ItemStatusFilter.vue'

var idx = 0;

export default {
  name: 'app',
  components: {
    AppHeader,
    TodoList,
    ItemAddForm,
    SearchPanel,
    ItemStatusFilter
  },
  data() {
    return {
      todoData: [
        this.createTodoItem('Drink Coffe'),
        this.createTodoItem('Code'),
        this.createTodoItem('Make App')
      ],
      term: '',
      filter: 'All'
    }
  },
  computed: {
    countDone: function() {
      return this.todoData.filter((el) => el.done).length;
    }
  },
  methods: {
    createTodoItem: function(label) {
      return {
        label: label,
        done: false,
        important: false,
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
    toggleImportantItem: function(id) {
      const idx = this.todoData.findIndex((el) => el.id === id);
      const el = this.todoData[idx];
      el.important = !el.important;
    },
    searchChange: function(term) {
      this.term = term;
    },
    searchItems: function (items, term) {
      if (!term.length) {
        return items;
      }
      return items.filter((el) => el.label.toLowerCase().indexOf(term.toLowerCase()) !== -1);
    },
    statusFilter: function(items, filter) {
      switch (filter) {
        case 'All':
          return items;
        case 'Active':
          return items.filter((el) => !el.done);
        case 'Done':
          return items.filter((el) => el.done);
        default:
          return items;
      }
    },
    visibleItems: function(items, term, filter) {
      const searched = this.searchItems(items, term);
      return this.statusFilter(searched, filter);
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

.top-panel {
  margin: 16px 0;
}

</style>
