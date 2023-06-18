<script>
export default {
  props: ["questions", "questionsAnswered"],
  emits: ["question-answered"],
  methods: {
    selectAnswer(is_correct) {
      this.$emit("question-answered", is_correct);
    },
  },
};
</script>

<template>
  <div class="questions-ctr">
    <div class="progress">
      <div
        class="bar"
        :style="{ width: `${(questionsAnswered / questions.length) * 100}%` }"
      ></div>
      <div class="status">
        {{ questionsAnswered }} de {{ questions.length }} preguntas respondidas
      </div>
    </div>
    <div
      class="single-question"
      v-for="(question, qi) in questions"
      :key="question.q"
      v-show="qi === questionsAnswered"
    >
      <div class="question">{{ question.q }}</div>
      <div class="answers">
        {{ /*hay que crear un componente para las respuestas*/  }}
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
