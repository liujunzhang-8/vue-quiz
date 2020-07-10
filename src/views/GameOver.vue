<template>
    <div class="h-100">
        <b-card-header class="custom-info text-white font-weight-bold">
            You Score: {{ score }} / {{ maxScore }}
        </b-card-header>
        <Answer v-for="(question, index) of questions" :key="index" :question="question"></Answer>
    </div>
</template>

<script>
import Answer from '../components/Answer'
export default {
    name: 'GameOver',
    components: {
        Answer
    },
    data() {
        return {
            score: 0,
            maxScore: 0,
            questions: []
        }
    },
    created() {
        this.setQuestions();
    },
    methods: {
        setQuestions() {
            this.questions = this.$root.$data.state || []
            this.$root.$data.state = []
            this.setScore()
        },
        setScore() {
            this.maxScore = this.questions.length * 10
            this.score = this.questions.filter(q => q.correct).length * 10
        }
    }
}
</script>

<style>

</style>