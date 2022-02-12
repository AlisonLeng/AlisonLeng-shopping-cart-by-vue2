<template>
  <div class="control-panel" id="btn-control">
    <button
      class="btn btn-outline"
      v-if="step >= 2"
      @click.stop.prevent="previousStep"
    >
      ← 上一步
    </button>
    <button
      class="btn btn-primary"
      v-if="step <= 2"
      @click.stop.prevent="nextStep"
    >
      下一步 →
    </button>
    <button class="btn-finish" v-if="step === 3">完成訂單</button>
  </div>
</template>

<script>
export default {
  props: {
    step: {
      type: Number,
      required: true,
    },
  },
  methods: {
    nextStep() {
      this.$emit("next-step", this.step);
    },

    previousStep() {
      this.$emit("previous-step", this.step);
    },
  },
};
</script>

<style lang="scss" scoped>
@import "../assets/scss/main.scss";
.control-panel {
  height: 100px;
  border-top: 1px solid $shopping_cart;
  margin-top: 32px;
  padding-top: 24px;
  display: flex;
  justify-content: space-between;
  grid-column: 1/9;
  grid-row: 2/3;
  width: 90%;
  margin: 0 80px;
  position: relative;

  .btn-outline {
    width: 77px;
    height: 40px;
    background-color: $bg_color;
    border-radius: 4px;
  }

  .btn-primary,
  .btn-finish {
    width: 157px;
    height: 40px;
    background-color: $btn_primary;
    border-radius: 4px;
    color: $bg_color;
    position: absolute;
    right: 0;
  }
}
</style>
