<script>
import Questions from "./components/Questions.vue";
import Results from "./components/Results.vue";
import data from "./data/data.js";
export default {
  name: "App",

  components: {
    Questions,
    Results,
  },
  data() {
    return {
      questionsAnswered: 0,
      totalCorrect: 0,
      questions: data.questions,
      results: data.results,
    };
  },
  methods: {
    questionAnswered(is_correct) {
      if (is_correct) {
        this.totalCorrect++;
      }
      this.questionsAnswered++;
    },
    reset() {
      this.questionsAnswered = 0;
      this.totalCorrect = 0;
    },
  },
};
</script>

<template>
  <div class="ctr">
    <Questions
      v-if="questionsAnswered < questions.length"
      :questions="questions"
      :questionsAnswered="questionsAnswered"
      @question-answered="questionAnswered"
    />
    <Results v-else :results="results" :totalCorrect="totalCorrect" />
    <button
      type="button"
      class="reset-btn"
      @click.prevent="reset"
      v-if="this.questionsAnswered === questions.length"
    >
      Reset
    </button>
  </div>
</template>

<style></style>
