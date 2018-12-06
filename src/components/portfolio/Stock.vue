<template>
  <div class="col-6">
    <div class="card mb-3">
      <div class="card-header">
        {{  stock.name }}
        <small>(Price: {{ stock.price }}) Quantity: {{ stock.quantity }}</small>
      </div>
      <div class="card-body">
        <div class="pull-left">
          <input 
            type="number"
            class="form-control"
            placeholder="Quantity"
            v-model="quantity">
        </div>
        <div class="pull-right">
          <button
            class="btn btn-info mt-2"
            @click="sellStock"
            :disabled="quantity <= 0 || !Number.isInteger(Number(quantity))">
            Sell
          </button>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import { mapActions } from "vuex"

export default {
  props: ["stock"],
  data() {
    return {
      quantity: 0
    }
  },
  methods: {
    ...mapActions({
      placeSellOrder: "sellStock"
    }),
    sellStock() {
      const order = {
        stockId: this.stock.id,
        stockPrice: this.stock.price,
        quantity: this.quantity
      }
      this.placeSellOrder(order);
      this.quantity = 0;
    }
  }
}
</script>
