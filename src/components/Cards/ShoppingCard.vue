<template>
<div class="card">
    <div class="wrap xl-flexbox xl-between xl-center product">
        <div class="col xl-1-7 sm-1-1">
            <div class="action">
                <Button size="sm full-radius" color="var(--border-color)" @click="() => $emit('delete',shoppingCart.id)">X</Button>
                <IconHearth color="red" width="28" height="25"/>
            </div>
        </div>

        <div class="col xl-2-7 sm-1-1">
            <img width="90" height="90" class="product-img" :src="shoppingCart.image" :alt="shoppingCart.title">
        </div>

        <div class="col xl-2-7 sm-1-1">
            <Text tag="p" size="lg">{{shoppingCart.title}}</Text>
            <Text tag="p" size="lg" color="var(--c-darkgray)">{{shoppingCart.subTitle}}</Text>
        </div>

        <div class="col xl-1-7 sm-1-2">
            <div class="quant">
                <Button @click="decreaseQuantity" size="sm full-radius" color="var(--c-darkgray)"><Text size="lg" color="white"> - </Text></Button>
                <Text>{{quantity}}</Text>
                <Button @click="increaseQuantity" size="sm full-radius" color="var(--c-darkgray)"><Text size="lg" color="white"> + </Text></Button>
            </div>
        </div>

        <div class="col xl-1-7 sm-1-2">
            <Text tag="h4" size="xl">{{shoppingCart.price}}$</Text>
        </div>
    </div>
</div>
</template>

<script>
import Text from '../Texts/Text.vue';
import IconHearth from '../icons/IconHearth.vue';
import Button from '../Buttons/Button.vue';

export default {
    components: { Text, IconHearth, Button },
    props: {
      shoppingCart: {
        type: Array,
        required: true
      }
    },
    computed: {
      quantity(){
        this.$emit('calulateTotalPrice', this.shoppingCart.price * this.shoppingCart.quantity)
        return this.shoppingCart.quantity
      }
    },
    methods: {
      decreaseQuantity(){
        this.shoppingCart.quantity !== 1 ? this.shoppingCart.quantity-- : 1
        
        this.$appAxios.patch(`/shoppingCart/${this.shoppingCart.id}`, {
          quantity: this.quantity
        }).then(res => res.data)
      },
      increaseQuantity(){
        this.shoppingCart.quantity++

        this.$appAxios.patch(`/shoppingCart/${this.shoppingCart.id}`, {
          quantity: this.quantity
        }).then(res => res.data)
      },
    }
}
</script>

<style scoped>
  .card{
    border-radius:10px;
    background: var(--card-bg);
    margin-bottom: 2.4em;
  }
  .header{
    padding: 1.5% 5%;
  }
  .product{
    padding: 24px 5%;
    border-top: 1px solid  #e3e6ea;
  }
  .quant{
    display:flex;
    justify-content: space-between;
    align-items: center;
  }
  .quant > * {
    margin: 0 8px;
  }
</style>