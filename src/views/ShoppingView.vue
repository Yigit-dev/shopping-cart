<template>
    <div class="wrap xl-gutter-40">
        <div class="col xl-9-12 lg-8-12 md-1-1">
            <ShoppingCard
                :shoppingCart="shoppingCart" 
                @delete="deleteFromCart"
                @quantity="setQuantity" />
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

export default {
    name: "ShoppingView",
    components: { ShoppingCard, TotalAmount },
    data(){
        return{
            shoppingCart: [],
            shippingPayment: 5,
            quantity: 1
        }
    },
    created(){
        this.getProductCart()
    },
    computed: {
        totalAmount(){
            let total = 0
            this.shoppingCart.forEach(item => {
                total += parseFloat(item.price * this.quantity, 10)
                total += this.shippingPayment
            });
            return {
                total: total.toFixed(2),
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
        setQuantity(quantity){
            this.quantity = quantity
        }
    }
}
</script>