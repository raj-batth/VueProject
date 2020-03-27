<template>
<b-col class="m-3">
    <b-card-group  deck>
        <b-card
        header-bg-variant="light"
        header-text-variant="dark"
        header-tag="header"
        >
        <template v-slot:header>
            {{stock.name}}: <small> (Price:{{stock.price}} | Quantiiy: {{stock.quantity}})</small>
        </template>
        <b-card-text >
            <input 
                type="number" 
                placeholder="Quantiiy" 
                class="float-left" 
                v-model.number = "quantity"> 
            <b-button 
                class="float-right" 
                variant="info" v-on:click="sellButtonClick"
                :disabled="insufficientQuantiy || quantity <= 0 || !Number.isInteger(this.quantity)"
                >
                {{insufficientQuantiy ? 'Not Enough Stocks' : 'Sell'}} 
            </b-button>
        </b-card-text>
       
        </b-card>
    </b-card-group>
</b-col>
</template>

<script>
import {mapActions} from 'vuex';

    export default {
        props:['stock'],
        data(){
            return{
                quantity:0
            }
        },
        methods:{
            ...mapActions([
                'sellStock'
            ]),
            sellButtonClick(){
                const order = {
                    stockId: this.stock.id,
                    stockPrice: this.stock.price,
                    quantity: this.quantity
                };
                this.sellStock(order);
                this.quantity = 0

            }
        },
        computed:{
            insufficientQuantiy(){
                return this.quantity > this.stock.quantity
            }
        }
    }
</script>