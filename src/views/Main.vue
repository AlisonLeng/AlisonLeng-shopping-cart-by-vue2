<template>
  <main>
    <div id="main-content">
      <!-- left form-->
      <div class="left-content">
        <!-- stepper -->
        <StepperPanel :step="step" />
        <!-- Form -->
        <div class="form-panel">
          <form id="form">
            <!-- FormStep1 -->
            <FormStep1 :step="step" />
            <!-- FormStep2 -->
            <FormStep2 :step="step" @FeeAmountChosen="handleFeeAmount" />
            <!-- FormStep3 -->
            <FormStep3 :step="step" />
          </form>
        </div>
      </div>
    </div>
    <!-- right content -->
    <div class="right-content">
      <!-- shopping cart  -->
      <ShoppingCart
        :initial-products="products"
        :delivery-fee="deliveryFee"
        @total="totalCart"
      />
    </div>
    <!-- StepButton -->
    <StepButton
      :step="step"
      @next-step="nextStep"
      @previous-step="previousStep"
    />
    <!-- Footer -->
    <Footer />
  </main>
</template>

<script>
import StepperPanel from "../components/StepperPanel.vue";
import FormStep1 from "../components/FormStep1.vue";
import FormStep2 from "../components/FormStep2.vue";
import FormStep3 from "../components/FormStep3.vue";
import ShoppingCart from "../components/ShoppingCart.vue";
import StepButton from "../components/StepButton.vue";
import Footer from "../components/Footer.vue";
import item1 from "../assets/img/item1.png";
import item2 from "../assets/img/item2.png";

const dummyData = {
  products: [
    {
      id: 1,
      name: "破壞補丁修身牛仔褲",
      price: 3999,
      quantity: 0,
      image: item1,
    },
    {
      id: 2,
      name: "刷色直筒牛仔褲",
      price: 1999,
      quantity: 0,
      image: item2,
    },
  ],
};

export default {
  name: "Main",
  components: {
    StepperPanel,
    FormStep1,
    FormStep2,
    FormStep3,
    ShoppingCart,
    StepButton,
    Footer,
  },
  data() {
    return {
      step: 1,
      products: [],
      total: 0,
      deliveryFee: 0,
    };
  },
  created() {
    this.fetchData();
  },
  methods: {
    fetchData() {
      this.products = dummyData.products;
    },
    nextStep() {
      return this.step++;
    },
    previousStep() {
      return this.step--;
    },
    handleFeeAmount(feeAmount) {
      this.deliveryFee = feeAmount;
    },
    totalAmount(payload) {
      console.log(payload);
    },
    totalCart(payload) {
      this.products = payload;
    },
  },
};
</script>

<style lang="scss" scoped>
@import "../assets/scss/main.scss";
main {
  width: 100%;
  position: absolute;
  top: 56px;
  display: grid;
  grid-template-columns: repeat(12, 1fr);
  grid-template-rows: 1fr auto 0.5fr;
  grid-gap: 20px;

  #main-content {
    width: 90%;
    margin: 80px;
    grid-column: 1/9;
  }
  .right-content {
    grid-column: 9/13;
    margin-top: 100px;
  }
}
</style>
