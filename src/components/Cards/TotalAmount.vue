<template lang="">
    <div class="card">
        <div class="card-title">
            <Text tag="h3" size="xl" fontWeight="700">The total amount of</Text>
        </div>
        <div class="wrap xl-flexbox xl-between">
            <div class="col">
                <Text tag="h4" size="lg">Temporary amount</Text>
            </div>
            <div class="col">
                <Text tag="h4" size="lg">${{totalAmount.total !== "0.00" ? totalAmount.total - totalAmount.shippingPayment : 0}}</Text>
            </div>
        </div>
        <div class="wrap xl-flexbox xl-between">
            <div class="col">
                <Text tag="h4" size="lg">Shipping</Text>
            </div>
            <div class="col">
                <Text tag="h4" size="lg">${{ totalAmount.shippingPayment }}</Text>
            </div>
        </div>
        <hr>
        <div class="wrap xl-flexbox xl-between">
            <div class="col">
                <Text tag="h4" size="lg" fontWeight="700">The total amount of</Text>
            </div>
            <div class="col">
                <Text tag="h4" size="lg" fontWeight="700">${{ totalAmount.total }}</Text>
            </div>
        </div>
        <Button size="xs" color="var(--c-purple)"><Text tag="h3" size="lg">Buy</Text></Button>
    </div>
</template>
<script>
import Button from '../Buttons/Button.vue';
import Text from '../Texts/Text.vue';

export default {
    name: 'TotalAmount',
    components: {Button,Text},
    props: {
        totalAmount: {
            type: String,
            default: "0.00",
            required: true,
        }
    }
}
</script>
<style scoped>
    .card{
        display: flex;
        flex-direction: column;
        padding: 36px;
        background-color: var(--card-bg);
        border-radius: 10px;
    }
    @media screen and (max-width: 768px){
        .card {
            margin-top: 4em;
        }
    }
    .card .card-title{
        margin-bottom: 16px;
    }
    .card button{
        margin: 36px 0 0;
    }
</style>