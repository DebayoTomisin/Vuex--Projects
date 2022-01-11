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
            <div v-for="(job, index) in jobs" :key="index" class="btn-container">
                <button v-on:click="setValue(index)" class="job-btn">{{job.company}}</button>
            </div>

            <article class="job-info">
                <h3>{{jobs[value].title}}</h3>
                <h4>{{jobs[value].company}}</h4>
                <p class="job-date">{{jobs[value].dates}}</p>
                <div v-for="(duty, index) in jobs[value].duties" :key="index" class="job-desc">
                    <p>{{duty}}</p>
                </div>
            </article>
        </div>
    </section>
</template>

<script>
    export default {
        name: 'Tabs',
        data() {
            return {
                jobs: [],
                value: 2,
                loading: true,
                url : 'https://course-api.com/react-tabs-project',

            }
        },
        methods: {
            async fetchJobs() {
                const response = await fetch(this.url)
                const data = await response.json(response)
                this.jobs = data
                this.loading = false
            },
            setValue(payload) {
                this.value = payload
            }
        },

        computed: {
        },
        created() {
            this.fetchJobs()
        }
    }
</script>

<style src='../assets/index.css'>

</style>