<template>
  <div class="form" v-show="step === 2" @change="FeeAmountChosen">
    <h2 class="form-title shipment">運送方式</h2>
    <div class="form-step-2">
      <div
        class="form-part"
        v-for="shipping in shippingList"
        :key="shipping.id"
      >
        <div class="description">
          <input
            type="radio"
            name="shipment"
            class="standard-select"
            :value="shipping.price"
            v-model="deliveryFee"
          />
          <label for="standard">
            <div class="ship-content method">{{ shipping.name }}</div>
            <div class="ship-content time">{{ shipping.period }}</div>
          </label>
        </div>
        <div class="ship-content-fee">{{ shipping.priceAmount }}</div>
      </div>
      <!-- <div class="form-part DHL">
        <div class="description">
          <input
            type="radio"
            name="shipment"
            id="DHL"
            class="DHL-select"
            :value="500"
            v-model="deliveryFee"
          />
          <label for="DHL">
            <div class="ship-content method">DHL 貨運</div>
            <div class="ship-content time">48小時內送達</div>
          </label>
        </div>

        <div class="ship-content-fee">$500</div>
      </div> -->
    </div>
  </div>
</template>

<script>
export default {
  name: "Delivery",
  props: {
    step: {
      type: Number,
      required: true,
    },
  },
  data() {
    return {
      shippingList: {
        standard: {
          name: "標準運送",
          period: "約 3~7 個工作天",
          price: 0,
          priceAmount: "免費",
          id: "standard",
          deliveryFee: 0,
        },
        dhl: {
          name: "DHL 貨運",
          period: "48 小時內送達",
          price: 500,
          priceAmount: "$500",
          id: "dhl",
          deliveryFee: 500,
        },
      },
      deliveryFee: 0,
    };
  },
  methods: {
    FeeAmountChosen() {
      this.$emit("FeeAmountChosen", this.deliveryFee);
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
  .form-step-2 {
    width: 70%;
    .form-part {
      display: flex;
      justify-content: space-between;
      align-items: center;
      border: 1px solid $shopping_cart;
      border-radius: 4px;
      padding: 10px;
      margin-top: 24px;
      cursor: pointer;
      &:hover,
      &:checked {
        border-color: $dark_gray;
      }

      .description {
        display: flex;
        align-items: center;
        width: 80%;
        margin-left: 10px;
        opacity: 1;

        input {
          z-index: 0;
          &[type="radio"] {
            -webkit-appearance: none;
            border: 1px solid $dark_gray;
            border-radius: 50%;
            padding: 0.5rem;
            cursor: pointer;
            &:checked {
              box-shadow: inset 0 0 0 0.3rem $dark_gray;
            }
          }
        }

        label {
          margin-left: 20px;
          & > div {
            font-weight: bold;
            font-size: 14px;
            color: $price_color;
          }

          :last-child {
            font-weight: normal;
            font-size: 12px;
            color: $price_color;
          }
        }
      }
    }
  }
}
</style>
