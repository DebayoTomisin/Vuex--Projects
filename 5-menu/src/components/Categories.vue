<template>
    <div class='btn-container' v-for="(cat, idx) in categories"  :key="idx">
        <button class="filter-btn" type="button" @click="filterCat(cat)">
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
       
   },
}

</script>

<style src='../assets/index.css' scoped>

</style>