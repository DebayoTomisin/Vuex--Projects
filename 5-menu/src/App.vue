<template>
  <main class="menu section">
    <div class="title">
      <h2>Our Menu</h2>
    </div>
    <div class="underline"></div>
  </main>
</template>

<script>
import Menu from './components/data'

export default {
  name: 'App',
  components: {
    
  },
  data(){
    return{
      menu : Menu
    }
  },
  created() {
    
  },
  methods: {

  }
}
</script>

<style src="./assets/index.css">

</style>