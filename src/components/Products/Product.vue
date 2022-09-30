<template>
    <div class="col"> 
        <div class="product-card">
          <img :src="product.image" :alt="product.title">
          <div class="product-card-hover-box">
            <div class="product-card-detail-box">
              <div class="product-info">
                <Text tag="h3" size="lg" color="#000">{{product.title}}</Text>
                <Text tag="h5" size="md" color="var(--c-darkgray)">{{product.subTitle}}</Text>  
              </div>
              <Button size="md" color="var(--c-orange)"
                v-if="!product.isPurchased && product.isStock" 
                @click="addToCart">
                <Text size="sm">ADD TO CART</Text>
              </Button>
              <Button size="xs" v-else-if="product.isPurchased" @click="deleteFromCart(product.id)">
                <IconCheck width="36" height="36" />
              </Button>
              <Button v-else size="md" color="var(--c-disabled)" disabled="true">
                <Text size="sm">No Stock</Text>
              </Button>
            </div>
          </div>
        </div>
    </div>
</template>

<script>
import Button from '../Buttons/Button.vue';
import Text from '../Texts/Text.vue';
import IconCheck from '../icons/IconCheck.vue';

export default {
    components: { Button, Text, IconCheck },
    props: {
        product: {
            type: Object,
            required: true
        }
    },
    methods:{
        addToCart(){
            this.product.isPurchased = true
            this.$appAxios.post('/shoppingCart', {...this.product})
                .then(() => {
                    this.$appAxios.patch(`/products/${this.product.id}`, {
                        isPurchased: true
                    }).then(res => res)
                })
                .catch(error => {
                    console.log(error)
                })
        },
        deleteFromCart(id){
            this.product.isPurchased = false
            this.$appAxios.delete(`/shoppingCart/${id}`).then(() => {
                this.$appAxios.patch(`/products/${this.product.id}`, {
                    isPurchased: false
                }).then(res => res)
            })
        },
    }
}
</script>
    
<style scoped>
.product-card {
    position:relative;
    margin: 1em 0 3em;
    display: flex;
    justify-content: center;
    align-items: center;
    border-radius: 16px;
}
.product-card:hover {
    background: var(--c-purple);
}
.product-card img{
    transition: all .2s ease-in-out;
}
.product-card img:hover {
    transform: scale(1.1);
}
.product-card-hover-box {
    display:none;
    width:100%;
    height:100%;
    position:absolute;
    top:10px; left:0;
    text-align:center;
    color:black;
}

.product-card-hover-box .product-card-detail-box {
    background: rgba(255,255,255,0.95);
    position:absolute;
    width: 35%;
    height:auto;
    left: 50%;
    transform: translate(-50%, -50%);
    top: 80%;
    padding: 1em;
    border-radius: 8px;
    display: flex;
    flex-direction: column;
    justify-content: center;
    align-items: center;
}
.product-card-hover-box .product-card-detail-box h5 {
    color:#b1b1b3;
}
.product-card:hover .product-card-hover-box {
    display:block;
}
.product-card:hover img {
    transform: scale(1.2);  
}
.product-card-hover-box p {
    display:inline-block;
    margin-left:2px;
    margin-right:2px;
}
.product-card-hover-box .product-card-detail-box .product-info{
    padding-bottom: 16px;
}
.product-card-detail-box button{
    width: 100%;
}
</style>