<template>
    <div class="questions-ctr">
        <div class="progress">
            <div class="bar"></div>
            <div class="status">{{ questionAnswered + 1 }} out of {{ questions.length }} questions answered</div>
        </div>
        <div class="single-question" v-for="(question, questionIndex) in questions" :key="question.q"
            v-show="questionAnswered === questionIndex">
            <div class="question">{{ question.q }}</div>
            <div class="answers" v-for="answer in question.answers" :key="answer.text" @click.prevent="chooseAnswer(answer.is_corrent)">
                <div class="answer">{{ answer.text }}</div>
            </div>
        </div>
    </div>
</template>

<script>
export default {
    props: ['questions', 'questionAnswered'],
    emit: ['chooseAnswer'],
    methods: {
        chooseAnswer(isCorrent) {
            this.$emit('chooseAnswer', isCorrent)
        }
    }
}
</script>
