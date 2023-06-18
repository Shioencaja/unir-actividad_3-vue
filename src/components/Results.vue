<script>
import ResultTitle from "./ResultTitle.vue";
import ResultDesc from "./ResultDesc.vue";
export default {
  props: ["results", "totalCorrect"],
  computed: {
    resultIndex() {
      let index = 0;
      this.results.forEach((e, i) => {
        if (e.min <= this.totalCorrect && e.max >= this.totalCorrect) {
          index = i;
        }
      });
      return index;
    },
  },
  components: { ResultTitle, ResultDesc },
};
</script>

<template>
  <div class="result">
    <ResultTitle :title="results[resultIndex].title" />
    <ResultDesc :desc="results[resultIndex].desc" />
  </div>
</template>
