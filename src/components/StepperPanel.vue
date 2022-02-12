<template>
  <div class="stepper-panel">
    <h2 class="stepper-title">結帳</h2>
    <div class="stepper-container">
      <div class="step active" :class="{ checked: step > 1 }">
        <div class="circle-container"></div>
        <div class="label-container">寄送地址</div>
      </div>
      <div
        class="step"
        :class="[{ active: step === 2 }, { checked: step === 3 }]"
      >
        <div class="circle-container"></div>
        <div class="connect-line" :class="{ bold: step >= 2 }"></div>
        <div class="label-container">運送方式</div>
      </div>
      <div class="step" :class="{ active: step === 3 }">
        <div class="circle-container"></div>
        <div class="connect-line" :class="{ bold: step >= 3 }"></div>
        <div class="label-container">付款資訊</div>
      </div>
    </div>
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
};
</script>

<style lang="scss" scoped>
@import "../assets/scss/main.scss";

.stepper-panel {
  width: 100%;
  .stepper-container {
    width: 80%;
    margin-top: 20px;
    display: flex;
    flex-direction: row;
    justify-content: space-between;
    text-align: center;
    .step {
      @include getStepNums(3);
      position: relative;

      .circle-container {
        width: 32px;
        height: 32px;
        color: $light_gray;
        background-color: $bg_color;
        border: 1px solid $light_gray;
        border-radius: 50%;

        &::after {
          position: absolute;
          top: 8px;
          left: 12px;
        }
      }

      .connect-line {
        position: absolute;
        width: 60px;
        height: 2px;
        background-color: $light_gray;
        right: 100px;
        bottom: 13px;
        &.bold {
          background-color: $dark_gray;
        }
      }

      .label-container {
        position: absolute;
        top: 6.5px;
        left: 30px;
        width: 90px;
      }

      &.active .circle-container {
        border-color: $dark_gray;
        &::after {
          color: $dark_gray;
        }
      }

      &.checked .circle-container {
        background-color: $dark_gray;
        border-color: $dark_gray;
        &::after {
          content: "\2714";
          color: $bg_color;
        }
      }
    }
  }
}
</style>
