<template>
    <div :key="person.id"  v-for="person in people">
        <h1>{{person.name}}</h1>
    </div>
</template>

<script>
    export default {
        name: 'Lists',
        props: {
            people: Array
        }
    }
    
</script>

<style scoped>

</style>