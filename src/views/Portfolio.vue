<template>
  <div class="portfolio">
    <b-container >
        <b-row class="mt-12">
          <PortStock
            v-for="stock in stocks" :stock="stock" 
            :key="stock.price "
          />
        </b-row>
        </b-container>
    
  </div>
</template>

<script>
import PortStock from '@/components/PortStock.vue'
import {mapGetters} from 'vuex'
export default {
  computed:{
    ...mapGetters({
      stocks: 'stockPortfolio'
    })
  },
  components:{
    PortStock,
  }
}
</script>
