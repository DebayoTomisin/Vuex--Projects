<template>
  <main>
    <section class="contiainer">
      <h2>Our Reviews </h2>
      <div class="underline"></div>
      <Reviews  />
    </section>
  </main>
</template>

<script>
import Reviews from './components/Reviews'

export default {
  name: 'App',
  components: {
    Reviews
  },
  
  
}
</script>

<style src="./assets/index.css">
</style>
