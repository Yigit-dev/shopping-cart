<template>
    <div class="wrap xl-3 md-2 sm-1">
      <Product v-for="product in products" :key="product.id" :product="product"/>
    </div>
</template>

<script>
import Product from '../Products/Product.vue';
export default {
    components: { Product },
    data(){
      return{
        products: []
      }
    },
    async created(){
      await this.$appAxios.get("/products").then(response => {
        this.products = response.data
      })
    },
}
</script>