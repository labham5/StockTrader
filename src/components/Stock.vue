<template>
    
        <b-col md="4" sm="6" style="margin:20px 0px">
            <b-card 
                border-variant="dark"
                :header="stock.name"
                header-bg-variant="dark"
                header-text-variant="white"
            >
                <b-card-text>Price:{{stock.price}}</b-card-text>
                <b-form>
                    <b-form-input
                        id="input-1"
                        type="number"
                        placeholder="Enter Quantity"
                        v-model="quantity"
                    ></b-form-input>
                <b-button variant="success" class="mt-3" @click="buyStock()"
                    :disabled="insufficientFunds ||quantity <= 0"
                >{{insufficientFunds?'Insufficient funds':'Buy-Stock'}}</b-button>
                </b-form>
            </b-card>
        </b-col>
</template>
<script>
export default {
    props:['stock'],
    data(){
        return{
            quantity: 1,
        }
    },
    computed:{
        insufficientFunds(){
            return this.quantity *this.stock.price > this.funds;
        },
        funds(){
            return this.$store.getters.funds;
        }
    },
    methods:{
        buyStock(){
            const number=parseInt(this.quantity);
            const order={
                stockId: this.stock.id,
                stockPrice: this.stock.price,
                quantity: number,
            }
            console.log(order);
            this.$store.dispatch('buyStocks',order);
            this.quantity=1;
        }
    }
}
</script>