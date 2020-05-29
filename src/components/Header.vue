<template>
    <div class="">
        
        <b-navbar toggleable="lg" type="dark" variant="dark" :sticky="true">
            <b-navbar-brand href="/#/">StockTrader</b-navbar-brand>

            <b-navbar-toggle target="nav-collapse"></b-navbar-toggle>

            <b-collapse id="nav-collapse" is-nav>
                <b-navbar-nav>
                    <b-nav-item href="/#/portfolio">Portfolio</b-nav-item>
                    <b-nav-item href="/#/stocks">Stocks</b-nav-item>
                </b-navbar-nav>

                <!-- Right aligned nav items -->
                <b-navbar-nav class="ml-auto">
                    
                    <b-nav-item href="#">
                        <b-button @click="endDay()" variant="outline-light">End Day</b-button>
                    </b-nav-item>
                    <b-nav-item-dropdown text="Save/Load" right>
                        <b-dropdown-item href="#">Save</b-dropdown-item>
                        <b-dropdown-item href="#">Load</b-dropdown-item>
                    </b-nav-item-dropdown>
                    <b-nav-item href="#" style="color:white">
                        <strong>
                            Funds:{{funds}}
                        </strong>
                    </b-nav-item>
                </b-navbar-nav>
            </b-collapse>
        </b-navbar>
    </div>
</template>

<script>
import {mapActions} from 'vuex'
export default {
  computed:{
    funds(){
      return this.$store.getters.funds;
    }
  },
  methods:{
      ...mapActions([
          'randomizeStocks'
      ]),
      endDay(){
        this.randomizeStocks();
      }
  }
}
</script>