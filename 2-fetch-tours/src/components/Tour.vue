<template>
    <article class="single-tour">
        <img :src="tour.image" :alt="tour.name" />
        <footer>
            <div class="tour-info">
                <h4>{{tour.name}}</h4>
                <h4 class="tour-price">${{tour.price}}</h4>
                <p v-if="readMore">
                    {{tour.info}}
                </p>
                <p v-else>
                    {{`${tour.info.substring(0, 100)}...`}} <button @click="setReadMore()"></button>
                </p>
            </div>
        </footer>
    </article>
</template>

<script>
export default {
  name: 'Tour',
  props: {
    tour: Object,
    removeTours: Function
  },

  data () {
    return {
      readMore: false
    }
  },

  methods: {
    setReadMore () {
      this.readMore = !this.readMore
    },
    onDelete (id) {
      this.$emit('delete-tour', id)
    }
  }

}
</script>

<style src="../assets/index.css" scoped>

</style>
