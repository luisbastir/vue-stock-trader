<template>
  <nav class="navbar navbar-expand-lg navbar-light bg-light">
    <router-link to="/" class="navbar-brand">Stock Trader</router-link>
    <div class="collapse navbar-collapse">
      <ul class="nav navbar-nav">
        <router-link to="/portfolio" activeClass="active" tag="li" class="nav-item"><a class="nav-link">Portfolio</a></router-link>
        <router-link to="/stocks" activeClass="active" tag="li" class="nav-item"><a class="nav-link">Stocks</a></router-link>
      </ul>
      <span class="navbar-text ml-3">Funds: {{ funds | currency }}</span>
      <ul class="navbar-nav ml-auto">
        <li class="nav-item"><a href="#" class="nav-link" @click="endDay">End Day</a></li>
        <li class="nav-item dropdown" :class="{show: isDropdownOpen}" @click="isDropdownOpen = !isDropdownOpen">
          <a
            class="nav-link dropdown-toggle"
            data-toggle="dropdown"
            role="button" aria-haspopup="true"
            aria-expanded="false">
            Save &amp; Load <span class="caret"></span>
          </a>
          <ul class="dropdown-menu" :class="{show: isDropdownOpen}">
            <li class="dropdown-item">Save Data</li>
            <li class="dropdown-item">Load Data</li>
          </ul>
        </li>
      </ul>
    </div>
  </nav>
</template>

<script>
import { mapActions } from "vuex"
export default {
  data() {
    return {
      isDropdownOpen: false
    }
  },
  computed: {
    funds() {
      return this.$store.getters.funds
    }
  },
  methods: {
    ...mapActions([
      "randomizeStocks"
    ]),
    endDay() {
      this.randomizeStocks()
    }
  }
}
</script>
