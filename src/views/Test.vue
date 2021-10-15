<template>
  <questions
    :questions="this.questions"
    @true-count="trueCount"
    :showAnswers="showAnswers"
  />
  <a @click="showResult()" class="btn btn-success mb-5 w-25">
    Save
  </a>
</template>
<script>
import Questions from "../components/Questions.vue";
export default {
  name: "Test",
  components: {
    Questions,
  },
  data() {
    return {
      questions: [],
      tCount: 0,
      showAnswers: false,
    };
  },
  methods: {
    async fetchQuestions() {
      const res = await fetch("api/question");
      const data = await res.json();
      console.log(data);
      return data;
    },
    trueCount: function(value) {
      this.tCount = value;
    },
    showResult() {
      alert(this.tCount * 20);
      this.showAnswers = true;
    },
  },
  async created() {
    this.questions = await this.fetchQuestions();
  },
};
</script>
