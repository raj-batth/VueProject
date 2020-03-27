<template>
<b-col class="m-3">
    <b-card-group  deck>
        <b-card
        header-bg-variant="light"
        header-text-variant="dark"
        header-tag="header"
        >
        <template v-slot:header>
            {{stock.name}}: (Price:{{stock.price}})
        </template>
        <b-card-text >
            <input 
                type="number" 
                placeholder="Quantiiy" 
                class="float-left" 
                v-model.number = "quantity"
                :class="{danger: insufficientFunds}"> 
            <b-button 
                class="float-right" 
                variant="success" v-on:click="buyButtonClick"
                :disabled="insufficientFunds || quantity <= 0 || !Number.isInteger(this.quantity)"
                >
                {{insufficientFunds ? 'Insufficient Funds' : 'Buy'}}
            </b-button>
        </b-card-text>
       
        </b-card>
    </b-card-group>
</b-col>
</template>

<script>
    export default {
        props:['stock'],
        data(){
            return{
                quantity:0
            }
        },
        methods:{
            buyButtonClick(){
                const order = {
                    stockId : this.stock.id,
                    stockPrice : this.stock.price,
                    quantity : this.quantity
                }
                // console.log(order)
                this.$store.dispatch('buyStock', order)
                this.quantity = 0
            }
        },
        computed:{
            funds(){
                return this.$store.getters.funds
            },
            insufficientFunds(){
                return this.quantity * this.stock.price > this.funds
            }
        }
    }
</script>
<style scoped>
.danger{
    border : 1px solid red;
}
</style>