<template>
    <section>
        <div class="title">
            <h2> Our Tours </h2>
            <div class="underline"></div>
            <div :key="tour.id" v-for="tour in tours">
              <Tour :tour="tour" :removeTour='removeTours' />
            </div>
        </div>
    </section>
</template>

<script>
import Tour from './Tour'
export default {
  name: 'Tours',

  props: {
    tours: Array,
    removeTours: Function
  },
  components: {
    Tour
  }
}

</script>

<style src="../assets/index.css" >

</style>
