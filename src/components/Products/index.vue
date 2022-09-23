<!-- 
<img src="https://i.ibb.co/sstC5z8/5.png" alt="5">  
          <img src="https://i.ibb.co/4VwfJMw/8.png" alt="8">
          <img src="https://i.ibb.co/Hd7jNH9/9.png" alt="9"> 

 -->
<template>
    <div class="wrap xl-3 md-2 sm-1">
      <Product v-for="i in 5"/>
    </div>
</template>

<script>
import Product from '../Products/Product.vue';
export default {
    components: { Product }
}
</script>