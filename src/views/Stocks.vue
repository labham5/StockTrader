<template>
    <div class="">
        <b-container >
        <b-row class="mt-12">
            <Stock
                v-for="stock in stocks"
                :key="stock.id"
                :stock="stock"
            />
        </b-row>
        </b-container>
    </div>

</template>

<script>
import Stock from '@/components/Stock.vue'
export default {
    components:{
        Stock,
    },
    computed:{
        stocks(){
            return this.$store.getters.stocks
        }
    }
}
</script>