<template>
    <div>
        <button @click="previousSlide" class="prev">-</button>
        <button @click="afterSlide" class="next">+</button>
    </div>
</template>

<script>
    export default {
        name: 'Button',         
        methods: {
            previousSlide() {
                this.$emit('previous-slide')
            },

            afterSlide () {
                this.$emit('next-slide')
            }
        },        
    }
</script>

<style>

</style>