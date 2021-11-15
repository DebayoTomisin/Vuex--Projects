<template>
    <article class='question'>
       <div>
            <h4>{{question.title}}</h4>
            <button class='btn' @click="$emit('toggleInfo')" v-if="showInfo"> - </button>
            <button class='btn' @click="$emit('toggleInfo')" v-else> + </button>
       </div>
       <p v-if='showInfo'>{{question.info}}</p>
    </article>
</template>

<script>
    export default {
        name: 'Question',
        props: {
            showInfo : Boolean,
            question: {
                info: String,
                title: String,
            },
        },
        emit : ['toggleInfo'],
    }
    
</script>

<style src="../assets/index.css">

</style>