<template>
    <div class="wrap xl-gutter-40">
        <div class="col xl-9-12 lg-8-12 md-1-1">
            <ShoppingCard v-for="i in 3"/>
        </div>
        <div class="col xl-3-12 lg-4-12 md-1-1">
            <TotalAmount />
        </div>
    </div>
</template>
<script>
import ShoppingCard from "../components/Cards/ShoppingCard.vue";
import TotalAmount from "../components/Cards/TotalAmount.vue";

export default {
    name: "ShoppingView",
    components: { ShoppingCard, TotalAmount }
}
</script>