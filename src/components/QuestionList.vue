<template>
    <div class="questions-ctr">
        <div class="progress">
            <div class="bar"></div>
            <div class="status">1 out of {{ questions.length }} questions answered</div>
        </div>
        <div class="single-question" v-for="(question, index) in questions" :key="question.q">
            <div class="question">{{ question.q }}</div>
            <div class="answers" v-for="answer in question.answers" :key="answer.text">
                <div class="answer">{{ answer.text }}</div>
            </div>
        </div>
    </div>
</template>

<script>
export default {
    props: ['questions']
}
</script>