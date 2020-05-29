<template>
    
        <b-col md="4" sm="6" style="margin:20px 0px">
            <b-card 
                border-variant="dark"
                :header="stock.name"
                header-bg-variant="dark"
                header-text-variant="white"
            >
                <b-card-text>Price:{{stock.price}} | Quantity:{{stock.quantity}} </b-card-text>
                <b-form>
                    <b-form-input
                        id="input-1"
                        type="number"
                        required
                        placeholder="Enter Quantity"
                        v-model="quantity"
                    ></b-form-input>
                <b-button variant="danger" class="mt-3" @click="sellStockLocal()"
                    :disabled="insufficientQuantity||quantity <= 0"
                >{{insufficientQuantity?'Not enough Stocks':'Sell-Stock'}}</b-button>
                </b-form>
            </b-card>
        </b-col>
</template>
<script>
import {mapActions} from 'vuex'

export default {
    props:['stock'],
    data(){
        return{
            quantity: 1,
        }
    },
    computed:{
        insufficientQuantity (){
            return this.quantity > this.stock.quantity;
        },
        funds(){
            return this.$store.getters.funds;
        }
    },
    methods:{
        ...mapActions(['sellStock']),
        sellStockLocal(){
            const order={
                stockId:this.stock.id,
                stockPrice: this.stock.price,
                quantity:this.quantity
            }
             this.sellStock(order);
             this.quantity=1;
        }
    }
}
</script>