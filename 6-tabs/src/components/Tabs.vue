<template>
    <section v-if="loading" class="section-loading">
        <h2>Loading... </h2>
    </section>
    <section v-if="!loading" class="section">
        <div class="title">
            <h2>Experience </h2>
            <div class="underline"></div>
        </div>
        
        <div class="jobs-center">
            
        </div>
    </section>
</template>

<script>
    export default {
        name: 'Tabs',
        data() {
            return {
                jobs: [],
                value: 0,
                loading: true,
                url : 'https://course-api.com/react-tabs-project',

            }
        },
        methods: {
            async fetchJobs() {
                const response = await fetch(this.url)
                const data = await response.json(response)
                this.jobs = data
            }
        },
        
        created() {
            this.fetchJobs()
            console.log(this.jobs)
            this.loading = false
        }
    }
</script>

<style src='../assets/index.css' scoped>

</style>