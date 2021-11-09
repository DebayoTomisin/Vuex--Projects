<template>
    <article :key="item.id" v-for='item in data' class="review">
       
        <div class="img-container">
            <img :src="item.image" :alt="item.name" class="person-img"/>
        </div>
        <h4 class="author">{{item.name}}</h4>
        <p class="job">{{item.job}}</p>
        <p class="info">{{item.info}}</p>

        <div class="button-container">
            <button class="prev-btn" @click="prevPerson()">Previous Btn</button>
            <button class="next-btn" @click="nextPerson()">Next Button</button>
            <button class="random-btn" @click="randomPerson()">surprise me</button>
        </div>
    </article>
</template>

<script>
    import reviewData from './data'

    export default {
        name: 'Reviews',
        data () {
            return{
                data: [],
                index: 0,
            }
        },
       
        methods: {
            checkNumbers (number) {
                if (number < 0){
                    return this.data.length
                }
                if (number > this.data.length - 1){
                    return 0
                }
                return number
            },

            randomPerson () {
                let randomNumber = Math.floor(Math.random() * this.data.length)
                if (randomNumber === this.index) {
                    randomNumber += 1
                }
                this.index = this.checkNumbers(randomNumber)
            },

            prevPerson () {
                this.index = () => {
                    let newIndex = this.index + 1
                    this.index = this.checkNumbers(newIndex)
                }
            },

            nextPerson () {
                this.index= () => {
                    let newIndex = this.index - 1
                    this.index = this.checkNumbers(newIndex)
                }
            },

        },
        
        created () {
            this.data = reviewData
        },
    }

</script>

<style src='../assets/index.css' >

</style>