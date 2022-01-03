<template>
    <section v-if="loading" class="section-loading">
        <h2>Loading... </h2>
    </section>
    <section v-if="!loading" class="dection">
        <h4>Make Room</h4>
    </section>
</template>

<script>
    export default {
        name: 'Tabs',
        data() {
            return {
                jobs: {},
                value: 0,
                loading: true,
                url : 'https://course-api.com/react-tabs-project',

            }
        },
        methods: {
            fetchJobs : async () => {
                const response = await fetch(this.url)
                const data = await response.json(response)

                this.jobs = data
                this.loading = false
            }
        },
        watch: {
            handler() {
                this.fetchJobs()
            }
        },
        mounted() {
            this.fetchJobs()
            console.log(this.jobs)
        }
    }
</script>

<style src='../assets/index.css' scoped>

</style>