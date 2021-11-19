<template>
    <!-- <div class="btn-container" :v-for="cat in categories">
        <button class="filter-btn" type='button'>
            {{ cat }}
        </button>
    </div> -->
    <div class='btn-container' :v-for="(cat, idx) in categories"  :key="idx">
        <button class="filter-btn" type="button" @click="$emit('flterCat()')">
           {{ cat }}
        </button>
    </div>

</template>

<script>
export default {
   name: 'Categories',
   props: {
       categories: Array,
       filterCat: Function,
   },
   created() {
       console.log('the listed categories', this.categories)
   },
   emit : ['filterCat']
}

</script>

<style src='../assets/index.css' scoped>

</style>