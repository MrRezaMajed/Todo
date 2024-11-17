<template>
  <header class="card">
    <h1>لیست وظایف </h1>
    <button id="theme-switcher">
      <img :src="sunImage" alt="Change color theme" />
    </button>
  </header>
</template>
<script>
import sun from '../assets/icon-sun.svg'
export default {
  data () {
    return {
      sunImage: sun
    }
  }
}
</script>
