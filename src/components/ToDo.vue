<template>
  <li class="card" draggable="true">
    <div class="cb-container">
      <input type="checkbox" :checked="todo.isCompleted ? true : null" class="cb-input"/>
      <span class="check"></span>
    </div>
    <p class="item">{{todo.title}}</p>
    <button class="clear">
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
  }
}
</script>
