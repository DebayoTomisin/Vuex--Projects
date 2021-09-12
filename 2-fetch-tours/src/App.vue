<template>
  <main v-if="tours.length === 0">
    <div>
      <h2>No Tours Left </h2>
      <button class='btn' onClick={this.fetchTours()}>refresh</button>
    </div>
  </main>

  <main v-else>
    <div v-if="loading === true">
      <Loading />
    </div>
    <div v-else>
      <Tours :tours="tours" @removeTour = "removeTour" />
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
    Loading
  },

  data () {
    return {
      loading: true,
      tours: []
    }
  },

  methods: {
    async fetchTours () {
      this.loading = false
      try {
        const response = await fetch(url)
        const tours = await response.json()
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
    },

    removeTour (id) {
      const newTours = this.tours.filter(tour => tour.id === id)
      this.tours = newTours
    }
  },

  async created () {
    this.loading = true
    await this.fetchTours()
  }

}

</script>

<style src="./assets/index.css" scoped>

</style>
