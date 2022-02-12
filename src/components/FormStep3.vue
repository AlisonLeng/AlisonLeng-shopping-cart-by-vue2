<template>
  <div class="form" v-show="step === 3">
    <h2 class="form-title payment">付款資訊</h2>
    <div class="form-step-3">
      <div class="form-part part-1">
        <div class="card-name">
          <label for="card-name">持卡人姓名</label>
          <input type="text" placeholder="請輸入持卡人姓名" />
        </div>
      </div>
      <div class="form-part part-2">
        <div class="card-number">
          <label for="card-number">卡號</label>
          <input type="text" placeholder="1111 2222 3333 4444" />
        </div>
      </div>
      <div class="form-part part-3">
        <div class="date">
          <label for="date">有效期限</label>
          <input type="text" placeholder="MM/YY" />
        </div>
        <div class="safe-number">
          <label for="safe-number">CVC/CCV</label>
          <input type="text" placeholder="123" />
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "Payment",
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
.form {
  margin-right: 50px;
  margin-top: 50px;

  .form-title {
    @extend %step-title;
    margin-bottom: 24px;
  }
  .form-step-3 {
    label {
      font-size: 12px;
      color: $label_color;
    }

    input,
    select {
      border: 1px solid $input_color;
      border-radius: 4px;
      font-size: 12px;
      padding: 12px;
      width: 100%;
    }

    & > .form-part > div {
      display: flex;
      flex-direction: column;
      margin-bottom: 24px;
    }

    :last-child {
      display: flex;
      flex-direction: row;
      justify-content: space-between;
      .date {
        width: 45%;
      }

      .safe-number {
        width: 45%;
      }
    }

    .part-1,
    .part-2 {
      width: 70%;
    }
  }
}
</style>
