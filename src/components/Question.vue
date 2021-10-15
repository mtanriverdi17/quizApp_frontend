<template>
  <div class="row my-5 px-2">
    <div class="col-12 col-md-7  mx-auto px-0 text-start">
      <h3 class="">Question {{ idx + 1 }}: {{ question.question }}</h3>
    </div>
    <div
      :key="choice.Id"
      class="col-12 col-md-7 mx-auto my-2 border text-start rounded-1 choice-div shadow-sm p-0"
      v-for="(choice, idx) in question.choices"
      :style="[
        selectedChoise == choice.id
          ? { background: 'rgb(230, 230, 230)' }
          : { background: 'white' },
      ]"
    >
      <Choice
        :choice="choice"
        :idx="idx"
        @selected-value="selectedValue"
        :sc="selectedChoise"
        :showAnswers="showAnswers"
      />
    </div>
  </div>
</template>
<script>
import Choice from "../components/Choice.vue";
export default {
  name: "Question",
  components: { Choice },
  data() {
    return {
      selectedChoise: 0,
    };
  },
  props: {
    question: Object,
    idx: Number,
    showAnswers: Boolean,
  },
  methods: {
    selectedValue(value) {
      this.selectedChoise = value;
      const array = [
        {
          qid: this.question.questionId,
          sid: this.selectedChoise,
        },
      ];
      this.$emit("selam", array);
    },
  },
};
</script>
