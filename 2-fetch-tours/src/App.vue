<template>
  <main v-if="tours.length === 0">
    <div>
      <h2>No Tours Left </h2>
      <button class='btn' onClick={this.fetchTours()}>refresh</button>
    </div>
  </main>
  <main v-else>
    <div v-if="loading">
      <Loading />
    </div>
    <div v-else>
      <Tours :tours="tours" />
    </div>
  </main>
</template>

<script>
import Tours from './components/Tours'
import Loading from './components/Loading'

const url = 'https://course-api.com/react-tours-project'

export default {
  name: 'App',
  components: {
    Tours,
    Loading
  },

  data () {
    return {
      loading: false,
      tours: []
    }
  },

  methods: {
    async fetchTours () {
      this.loading = true
      try {
        const response = await fetch(url)
        const tours = await response.json()
        console.log(tours)
        this.tours = tours
        console.log('the fetch was a succcess')
      } catch (error) {
        console.log('error occupied')
      }
    },

    getTours () {
      if (this.loading) {
        return (
          <Loading />
        )
      } else {
        return (
          <Tours tours={this.tours} />
        )
      }
    },

    noTours () {
      return (
        <div><h2>No Tours Left </h2> <button class='btn' onClick={this.fetchTours()}>refresh</button> </div>
      )
    }
  },

  async created () {
    this.loading = false
    await this.fetchTours()
  }

}

</script>

<style src="./assets/index.css" scoped>

</style>
