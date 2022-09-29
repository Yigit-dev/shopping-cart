<template>
    <div class="wrap xl-gutter-40">
        <div class="col xl-9-12 lg-8-12 md-1-1"> 
            <Text tag="h3" size="xl">Shopping Bag: {{shoppingCart.length}}</Text>
            <ShoppingCard
                v-for="cart in shoppingCart"
                :shoppingCart="cart"
                @delete="deleteFromCart" 
                @calulateTotalPrice="calulateTotalPrice"/>
        </div>
        <div class="col xl-3-12 lg-4-12 md-1-1">
            <TotalAmount 
                :totalAmount="totalAmount" />
        </div>
    </div>
</template>
<script>
import ShoppingCard from "../components/Cards/ShoppingCard.vue";
import TotalAmount from "../components/Cards/TotalAmount.vue";
import Text from "../components/Texts/Text.vue";

export default {
    name: "ShoppingView",
    components: { ShoppingCard, TotalAmount, Text },
    data(){
        return{
            shoppingCart: [],
            shippingPayment: 5,
            totalPrice: 0
        }
    },
    created(){
        this.getProductCart()
    },
    computed: {
        totalAmount(){
            let total = 0
            this.shoppingCart.forEach(item => {
                total += parseFloat(item.price, 10) * item.quantity
            });
            return {
                total: total,
                shippingPayment: this.shippingPayment
            }
        }
    },
    methods: {
        async getProductCart(){
            await this.$appAxios.get('/shoppingCart').then(response => {
                this.shoppingCart = response.data
            })
        },
        deleteFromCart(id){
            this.$appAxios.delete(`/shoppingCart/${id}`).then(() => {
                this.getProductCart()
            })
        },
        calulateTotalPrice(price){
            this.totalPrice += price
        }
    }
}
</script>