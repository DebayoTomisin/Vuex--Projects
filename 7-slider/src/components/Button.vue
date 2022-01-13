<template>
    <div>
        <button class="prev">-</button>
        <button class="next">+</button>
    </div>
</template>

<script>
    export default {
        name: 'Button',
        data() {
            return {

            }
        },
        props: ["prevSlide", "nextSlide"],            
        methods: {},
        created() {},
    }
</script>

<style>

</style>