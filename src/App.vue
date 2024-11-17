<template>
  <HeaderComponent></HeaderComponent>
  <main>
    <add-todo @AddNewTodo="AddTodo"></add-todo>
    <ul class="todos">
      <to-do v-for="(item, index) in todos" :key="index" :todo="item"></to-do>
    </ul>
    <div class="card stat">
      <p class="corner"><span id="items-left">0</span> مورد باقی مانده</p>
      <div class="filter">
        <button id="all" class="on">همه</button>
        <button id="active">فعال</button>
        <button id="completed">تکمیل</button>
      </div>
      <div class="corner">
        <button id="clear-completed">حذف تکمیل شده ها</button>
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
      todos: [
        { title: 'Java', isCompleted: false },
        { title: 'Asp.net', isCompleted: true }
      ]
    }
  },
  methods: {
    AddTodo (title) {
      const todo = { title, isComplete: false }
      this.todos.push(todo)
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
