<template>
  <div class="container" v-if="showAnswers">
    <div class="row my-5 px-2">
      <div
        class="col-12 col-md-7 mx-auto px-0 text-start"
        style="color:#4E9F3D"
      >
        <h2>Your score is: {{ this.tCount * 20 }} out of 100</h2>
        <h3>You can see correct answers below</h3>
      </div>
    </div>
  </div>

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
      // alert(this.tCount * 20);
      window.scrollTo(0, 0);
      this.showAnswers = true;
    },
  },
  async created() {
    this.questions = await this.fetchQuestions();
  },
};
</script>
