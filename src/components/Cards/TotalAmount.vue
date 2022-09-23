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
                <Text tag="h4" size="lg">$24</Text>
            </div>
        </div>
        <div class="wrap xl-flexbox xl-between">
            <div class="col">
                <Text tag="h4" size="lg">Shipping</Text>
            </div>
            <div class="col">
                <Text tag="h4" size="lg">$5</Text>
            </div>
        </div>
        <hr>
        <div class="wrap xl-flexbox xl-between">
            <div class="col">
                <Text tag="h4" size="lg" fontWeight="700">The total amount of</Text>
            </div>
            <div class="col">
                <Text tag="h4" size="lg" fontWeight="700">$29</Text>
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
    components: {Button,Text}
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