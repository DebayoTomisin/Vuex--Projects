<template>
    <article :class="position">
        <img :src="(`${people[value].image}`)" alt="image" class="person-img" />
        <h4>{{ people[value].name }}</h4>
        <p className="title">{{people[value].title}}</p>
        <p className="text">{{people[value].quote}}</p>
    </article>
</template>

<script>
    export default {
        name: 'People',
        data(){
            return{
                position: 'activeSlide',
                value: this.index
            }
        },
        props: ['people', 'index'],
        computed: {},
        // methods: {
        //     getValue(){
        //         let position = 'nextSlide'
        //         this.people.map((person, personIndex) => {
        //             if(personIndex == this.value){
        //                 position = "activeSlide"
        //             }
                    
        //             if(personIndex === this.value - 1 || (this.value == 0 && personIndex === this.people.length - 1)) {
        //                 position= "lastSlide"
        //             }
        //         })
        //         return position
        //     }
            
        // },
        // updated () {
        //     this.position = this.getValue()
        //     console.log(this.position)
        // },
    }
</script>

<style>

</style>