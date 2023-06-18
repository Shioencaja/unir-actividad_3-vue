<script>
import QuestionHeader from "./QuestionHeader.vue";
export default {
  components: { QuestionHeader },
  props: ["questions", "questionsAnswered"],
  emits: ["question-answered"],
  methods: {
    selectAnswer(is_correct) {
      this.$emit("question-answered", is_correct);
    },
  },
  components: { QuestionHeader },
};
</script>

<template>
  <div class="questions-ctr">
    <QuestionHeader
      :questions="questions"
      :questionsAnswered="questionsAnswered"
    />
    <div
      class="single-question"
      v-for="(question, qi) in questions"
      :key="question.q"
      v-show="qi === questionsAnswered"
    >
      <div class="question">{{ question.q }}</div>
      <div class="answers">
        <div
          class="answer"
          v-for="answer in question.answers"
          :key="answer.text"
          @click.prevent="selectAnswer(answer.is_correct)"
        >
          {{ answer.text }}
        </div>
      </div>
    </div>
  </div>
</template>
