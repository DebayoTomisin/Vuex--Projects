<template>
    <article class="review">
       
        <div class="img-container">
            <img :src="info.image" :alt="info.name" class="person-img"/>
        </div>
        <h4 class="author">{{info.name}}</h4>
        <p class="job">{{info.job}}</p>
        <p class="info">{{info.info}}</p>

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
                info: {}
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
                console.log(this.index)
            },

            // prevPerson () {
            //     this.index = () => {
            //         let newIndex = this.index + 1
            //         this.index = this.checkNumbers(newIndex)
            //         console.log(this.index)
            //     } 
            // },

            prevPerson () {
                let newIndex
                newIndex = this.index - 1
                this.index = this.checkNumbers(newIndex)
            },


            nextPerson () {
                let newIndex
                newIndex = this.index + 1
                this.index = this.checkNumbers(newIndex)
            }

        },

        beforeCreate() {
            console.log('before create hook has been called')
        },

        created() {
            alert(`the current index value is: ${this.index}`)
        },
        
        mounted () {
            this.data = reviewData
            this.info = this.data[this.index]
            {{console.log(this.index)}}
        },
        updated() {
            this.info = this.data[this.index]
        }
    }

</script>

<style src='../assets/index.css'>

</style>