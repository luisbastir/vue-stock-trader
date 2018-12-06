<template>
  <div class="col-6">
    <div class="card mb-3">
      <div class="card-header">
        {{  stock.name }}
        <small>(Price: {{ stock.price }})</small>
      </div>
      <div class="card-body">
        <div class="pull-left">
          <input 
            type="number"
            class="form-control"
            placeholder="Quantity"
            v-model="quantity"
            :class="{danger: insufficientFunds}">
        </div>
        <div class="pull-right">
          <button
            class="btn btn-success mt-2"
            @click="buyStock"
            :disabled="insufficientFunds || quantity <= 0 || !Number.isInteger(Number(quantity))">
            {{ insufficientFunds ? "Insufficient Funds" : "Buy" }}
          </button>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  props: ["stock"],
  data() {
    return {
      quantity: 0
    }
  },
  computed: {
    funds() {
      return this.$store.getters.funds
    },
    insufficientFunds() {
      return this.quantity * this.stock.price > this.funds;
    }
  },
  methods: {
    buyStock() {
      const order = {
        stockId: this.stock.id,
        stockPrice: this.stock.price,
        quantity: Number(this.quantity)
      };
      this.$store.dispatch("buyStock", order);
      this.quantity = 0;
    }
  }
}
</script>

<style scoped>
.danger {
  border: 1px solid red;
}
</style>

