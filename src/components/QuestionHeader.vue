<script>
export default {
  props: ["questions", "questionsAnswered"],
};
</script>
<template>
  <div class="progress">
    <div
      class="bar"
      :style="{ width: `${(questionsAnswered / questions.length) * 100}%` }"
    ></div>
    <div class="status">
      {{ questionsAnswered }} de {{ questions.length }} preguntas respondidas
    </div>
  </div>
</template>
