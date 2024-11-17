<template>
  <li class="card" draggable="true">
    <div class="cb-container">
      <input @click="changeStatus" type="checkbox" :checked="todo.isCompleted ? true : null" class="cb-input"/>
      <span class="check"></span>
    </div>
    <p class="item">{{todo.title}}</p>
    <button @click="deleteTodo" class="clear">
      <img :src="crossImage" alt="clear it"/>
    </button>
  </li>
</template>
<script>
import cross from '../assets/icon-cross.svg'
export default {
  props: {
    todo: Object
  },
  data () {
    return {
      crossImage: cross
    }
  },
  methods: {
    deleteTodo () {
      if (confirm('آیا از حذف اطمینان دارید؟')) {
        this.$emit('Deleted', this.todo.id)
      }
    },
    changeStatus () {
      this.$emit('changeStatus', this.todo.id, !this.todo.isCompleted)
    }
  }
}
</script>
