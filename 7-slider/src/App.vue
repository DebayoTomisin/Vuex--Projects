<template>
  <section class="section">
    <div class="title"> <h2><span>/</span>Reviews</h2></div>
    <div class="section-center">
      
    </div>
  </section>
</template>

<script>
import data from './components/data'
export default {
  name: 'App',
  components: {
  },
  data() {
    return {
      peopleData: data,
      index: 0
    }
  },

  methods: {
    setIndex (payload) {
      let index = payload - 1
      if (index < 0) {
        index = this.people.length - 1
      }
      return index
    },

    setSlider () {

    }
  },
  computed () {
    this.index = this.setIndex
  },

  watch() {
    "index", function () {
      this.setSlider()
    }
  },
  created() {
    
  }
}
</script>

<style src="./assets/index.css">
</style>
