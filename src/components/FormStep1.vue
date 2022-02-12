<template>
  <div class="form" v-show="step === 1">
    <h2 class="form-title address">寄送地址</h2>
    <div class="form-step-1">
      <div class="form-part">
        <div class="form-part-title">
          <label for="name-title">稱謂</label>
          <div class="select-wrapper">
            <select name="name-title" id="name-title" required>
              <option value="" disabled-selected>稱謂</option>
              <option value="male">先生</option>
              <option value="male">女士</option>
            </select>
          </div>
        </div>
        <div class="name">
          <label for="name">姓名</label>
          <input type="text" placeholder="請輸入姓名" />
        </div>
      </div>
      <div class="form-part">
        <div class="phone">
          <label for="phone">電話</label>
          <input type="text" placeholder="請輸入電話" />
        </div>

        <div class="email">
          <label for="email">Email</label>
          <input type="text" placeholder="請輸入電子郵件" />
        </div>
      </div>
      <div class="form-part">
        <div class="city">
          <label for="city">縣市</label>
          <div class="select-wrapper">
            <select name="city" id="city" required>
              <option value="" disabled-selected>請選擇縣市</option>
              <option value="">台北市</option>
              <option value="">新北市</option>
              <option value="">桃園市</option>
              <option value="">台中市</option>
              <option value="">台南市</option>
              <option value="">高雄市</option>
            </select>
          </div>
        </div>
        <div class="address">
          <label for="address">地址</label>
          <input type="text" placeholder="請輸入地址" />
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "Address",
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
  width: 100%;
  .form-title {
    @extend %step-title;
    margin-bottom: 24px;
  }
  .form-step-1 {
    width: 100%;
    margin-top: 20px;
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

    select {
      &:invalid {
        color: $light_gray;
      }
      cursor: pointer;
    }

    & > .form-part > div {
      display: flex;
      flex-direction: column;
      margin-bottom: 24px;
    }

    .form-part {
      display: grid;
      grid-template-columns: repeat(6, 1fr);
      grid-gap: 30px;
      &-title,
      .city {
        width: 100%;
        grid-column: 1/3;
      }

      .name,
      .address {
        width: 100%;
        margin: 0px;
        grid-column: 3/7;
      }

      .phone {
        grid-column: 1/4;
      }

      .email {
        grid-column: 4/7;
      }
    }
  }
}
</style>
