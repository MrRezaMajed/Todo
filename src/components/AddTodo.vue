<template>
  <div class="card add">
      <div class="cb-container">
        <button @click="AddTodo" id="add-btn">+</button>
      </div>
      <div class="txt-container">
        <label for="addt">افزودن </label>
        <input v-model="todoTitle" @keypress.enter="AddTodo" type="text" class="txt-input" placeholder="افزودن وظیفه جدید..." spellcheck="false" autocomplete="off"
          id="addt" dir="rtl" />
      </div>
    </div>
</template>
<script>
export default {
  data () {
    return {
      todoTitle: ''
    }
  },
  methods: {
    AddTodo () {
      this.$emit('AddNewTodo', this.todoTitle)
      this.todoTitle = ''
    }
  }
}
</script>
