<template>
    <div>
        <button @click="previousSlide" class="prev">-</button>
        <button @click="afterSlide" class="next">+</button>
    </div>
</template>

<script>
    export default {
        name: 'Button',
        data() {
            return {

            }
        },          
        methods: {},
        props:["previousSlide", "afterSlide"],
        mounted(){
            this.previousSlide(),
            this.afterSlide()
        },

        created() {
            this.$emit('created')
        },
    }
</script>

<style>

</style>