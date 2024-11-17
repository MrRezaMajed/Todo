<template>
  <HeaderComponent></HeaderComponent>
  <main>
    <add-todo @AddNewTodo="AddTodo"></add-todo>
    <ul class="todos">
      <to-do v-for="(item, i) in todos"
       :key="item.id" :todo="item"
       @Deleted="DeleteTodo"
       @changeStatus="changeTodoStatus"
       @dragstart="dragStart(i)"
       @drop="drop(i)"
       @dragover.prevent>
      </to-do>
    </ul>
    <div class="card stat">
      <p class="corner"><span id="items-left">{{getActiveTodoCount}}</span> مورد باقی مانده</p>
      <div class="filter">
        <button id="all" class="on">همه</button>
        <button id="active">فعال</button>
        <button id="completed">تکمیل</button>
      </div>
      <div class="corner">
        <button @click="deleteCompleted" id="clear-completed">حذف تکمیل شده ها</button>
      </div>
    </div>
  </main>
  <footer-component></footer-component>
</template>

<script>
import HeaderComponent from './components/HeaderComponent.vue'
import FooterComponent from './components/FooterComponent.vue'
import AddTodo from './components/AddTodo.vue'
import ToDo from './components/ToDo.vue'

export default {
  name: 'App',
  components: { HeaderComponent, FooterComponent, AddTodo, ToDo },
  data () {
    return {
      todos: [],
      dragging: -1
    }
  },
  computed: {
    getActiveTodoCount () {
      return this.todos.filter(f => f.isCompleted === false).length
    }
  },
  methods: {
    AddTodo (title) {
      const id = Math.random().toString(16).slice(2)
      const todo = { id, title, isCompleted: false }
      this.todos.push(todo)
    },
    DeleteTodo (id) {
      this.todos = this.todos.filter(f => f.id !== id)
    },
    changeTodoStatus (id, newStatus) {
      var newTodos = [...this.todos]
      var selectedTodo = newTodos.find(f => f.id === id)
      selectedTodo.isCompleted = newStatus
      this.todos = newTodos
    },
    deleteCompleted (id) {
      if (confirm('آیا از حذف اطمینان دارید؟')) {
        var newTodos = [...this.todos]
        newTodos = newTodos.filter(f => f.isCompleted === false)
        this.todos = newTodos
      }
    },
    dragStart (index) {
      this.dragging = index
    },
    drop (index) {
      var newElement = this.todos.splice(this.dragging, 1)[0]
      this.todos.splice(index, 0, newElement)
    }
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
