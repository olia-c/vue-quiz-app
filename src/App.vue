<template>
  <div class="ctr">
    <question-list 
      v-if="questionAnswered < questions.length" 
      :questions="questions" 
      :questionAnswered="questionAnswered" 
      @chooseAnswer="chooseAnswer"
    />
    <result-section v-else :result="result" />
    <button type="button" class="reset-btn" @click.prevent="resetToDefault">Reset</button>
  </div>
</template>


<script>
import QuestionList from './components/QuestionList.vue'
import ResultSection from './components/ResultSection.vue'

const defaultQuestions = [
  {
    q: 'What is 2 + 2?',
    answers: [
      {
        text: '4',
        is_correct: true
      },
      {
        text: '3',
        is_correct: false
      },
      {
        text: 'Fish',
        is_correct: false
      },
      {
        text: '5',
        is_correct: false
      }
    ]
  },
  {
    q: 'How many letters are in the word "Banana"?',
    answers: [
      {
        text: '5',
        is_correct: false
      },
      {
        text: '7',
        is_correct: false
      },
      {
        text: '6',
        is_correct: true
      },
      {
        text: '12',
        is_correct: false
      }
    ]
  },
  {
    q: 'Find the missing letter: C_ke',
    answers: [
      {
        text: 'e',
        is_correct: false
      },
      {
        text: 'a',
        is_correct: true
      },
      {
        text: 'i',
        is_correct: false
      }
    ]
  },
];
const defaultResults = [
  {
    min: 0,
    max: 2,
    title: "Try again!",
    description: "Do a little more studying and you may succeed!"
  },
  {
    min: 3,
    max: 3,
    title: "Wow, you're a genius!",
    description: "Studying has definitely paid off for you!"
  }
];

export default {
  name: 'App',
  components: {
    QuestionList, ResultSection
  },
  data() {
    return {
        questions: defaultQuestions,
        results: defaultResults,
        questionAnswered: 0,
        correntAnswers: 0,
    }
  },
  computed: {
    result() {
      return this.results.find(result => this.correntAnswers >= result.min && this.correntAnswers <= result.max)
    }
  },
  methods: {
    chooseAnswer(isCorrent) {
      this.questionAnswered++;
      if (isCorrent) {
        this.correntAnswers++;
      }
    },
    resetToDefault() {
      this.questionAnswered = 0;
      this.correntAnswers = 0
    }
  }
};

</script>

<style scoped>

</style>
