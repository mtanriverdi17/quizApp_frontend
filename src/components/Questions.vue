<template>
  <div
    :key="question.questionId"
    v-for="(question, index) in questions"
    class="container"
  >
    <Question
      :question="question"
      :idx="index"
      @selam="addToArray"
      :showAnswers="showAnswers"
    />
  </div>
</template>
<script>
import Question from "./Question.vue";
export default {
  name: "Questions",
  props: {
    questions: Array,
    showAnswers: Boolean,
  },
  components: {
    Question,
  },
  data() {
    return {
      answers: [
        {
          id: this.questions[0].questionId,
          val: false,
        },
        {
          id: this.questions[1].questionId,
          val: false,
        },
        {
          id: this.questions[2].questionId,
          val: false,
        },
        {
          id: this.questions[3].questionId,
          val: false,
        },
        {
          id: this.questions[4].questionId,
          val: false,
        },
      ],
    };
  },
  methods: {
    addToArray: function(value) {
      this.answers.find((x) => x.id == value[0].qid).val = this.questions
        .find((x) => x.questionId == value[0].qid)
        .choices.find((x) => x.id == value[0].sid).isCorrect;

      this.$emit(
        "true-count",
        this.answers.filter((x) => x.val == true).length
      );
    },
  },
};
</script>
