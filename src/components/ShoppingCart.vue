<template>
  <div class="right-content">
    <div class="shopping-cart-panel">
      <div class="cart-title">購物籃</div>
      <div class="shopping-cart-items">
        <div class="item" v-for="product in products" :key="product.id">
          <img :src="product.image" alt="" />
          <div class="item-introduce">
            <div class="item-name">{{ product.name }}</div>
            <div class="item-amount">
              <div class="item-minus" @click.stop.prevent="minusItem(product)">
                -
              </div>
              <div class="item-quantity">{{ product.quantity }}</div>
              <div class="item-plus" @click.stop.prevent="addItem(product)">
                ＋
              </div>
            </div>
            <div class="item-price">${{ product.price }}</div>
          </div>
        </div>
        <div class="shipping-fee">
          <div>運費</div>
          <div class="freight-price">
            {{ deliveryFee | presentDeliveryFee }}
          </div>
        </div>
        <div class="total">
          <div>小計</div>
          <div>${{ sum }}</div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  props: {
    initialProducts: {
      type: Array,
      required: true,
    },
    deliveryFee: {
      type: Number,
      required: true,
    },
  },
  data() {
    return {
      products: [],
      totalPrice: 0,
    };
  },
  created() {
    this.fetchData();
  },
  methods: {
    fetchData() {
      this.products = this.initialProducts;
    },
    addItem(product) {
      product.quantity++;
      this.totalAmount();
      this.checkTotalPrice();
    },
    minusItem(product) {
      if (!product.quantity) {
        alert("已達商品最少購買數量");
        return;
      }
      product.quantity--;
      this.totalAmount();
      this.checkTotalPrice();
    },
    totalAmount() {
      this.$emit("total", this.products);
    },

    checkTotalPrice() {
      let total = 0;
      this.products.forEach(
        (product) => (total += product.quantity * product.price)
      );
      this.totalPrice = total;
    },
  },
  filters: {
    presentDeliveryFee(fee) {
      if (fee === 0) {
        return "免費";
      }
      return "$" + fee;
    },
  },
  computed: {
    sum() {
      return this.totalPrice + this.deliveryFee;
    },
  },
};
</script>

<style lang="scss" scoped>
@import "../assets/scss/main.scss";

.shopping-cart-panel {
  border: 1px solid $shopping_cart;
  border-radius: 8px;
  width: 90%;
  padding: 1rem;
  margin-top: 24px;
  margin-right: 65px;

  .cart-title {
    font-weight: bold;
    font-size: 18px;
    color: $dark_gray;
    padding-bottom: 12px;
  }

  .shopping-cart-items {
    .item {
      margin-bottom: 30px;
      display: flex;
      flex-direction: row;
      justify-content: space-between;
      img {
        width: 100px;
      }
      .item-introduce {
        display: flex;
        flex-direction: column;
        align-items: end;

        .item-name {
          font-family: Noto Sans TC;
          font-style: normal;
          font-weight: normal;
          font-size: 16px;
          line-height: 24px;
          color: $dark_gray;
        }

        .item-amount {
          width: 100px;
          display: flex;
          flex-direction: row;
          justify-content: space-between;
          align-items: center;
          padding-top: 1rem;
          .item-minus,
          .item-plus {
            width: 26px;
            height: 27px;
            background-color: $shopping_cart;
            border-radius: 50%;
            text-align: center;
            padding-top: 4px;
            cursor: pointer;
          }
        }

        .item-price {
          padding-top: 1rem;
          font-family: Nunito Sans;
          color: $price_color;
          font-weight: bold;
          font-size: 16px;
        }
      }
    }

    .item-2 {
      margin-top: 18px;
    }

    .shipping-fee,
    .total {
      display: flex;
      justify-content: space-between;
      border-top: 1px solid $shopping_cart;
      margin-top: 1rem;
      padding-top: 1rem;

      :last-child {
        font-family: Nunito Sans;
        color: $price_color;
        font-weight: bold;
        font-size: 14px;
      }
    }
  }
}
</style>
