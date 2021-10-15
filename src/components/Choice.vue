<template>
  <div
    @click="changeBackground(this.choice.id)"
    class="py-2 d-flex choice-div  "
  >
    <div class="circle">{{ idx + 1 }}</div>
    <div class="choice-text mx-2">
      <span>{{ this.choice.choiceText }}</span>
    </div>
  </div>
</template>
<script>
export default {
  name: "choices",
  props: {
    choice: Object,
    idx: Number,
    sc: Number,
  },
  data() {
    return {};
  },
  methods: {
    changeBackground(choiceId) {
      this.$emit("clicked-zart", choiceId);
    },
  },
};
</script>
<style scoped>
.choice-div {
  cursor: pointer;
}

.choice-text {
  width: 90%;
  line-height: 25px;
}
.circle {
  background: rgb(231, 230, 230);
  width: 25px;
  height: 25px;
  border-radius: 50%;
  display: flex; /* or inline-flex */
  align-items: center;
  justify-content: center;
}
</style>
