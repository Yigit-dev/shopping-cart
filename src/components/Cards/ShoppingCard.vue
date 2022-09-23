<template>
<div class="card">
    <div class="header">
        <Text tag="h3" size="xl">Shopping Bag Total : <span id="tot">0</span> $</Text>
    </div>
    <div class="wrap xl-flexbox xl-between xl-center product">
        <div class="col sm-1-1">
            <div class="action">
                <Button size="sm full-radius" color="var(--border-color)">X</Button>
                <IconHearth color="red" width="28" height="25"/>
            </div>
        </div>

        <div class="col sm-1-1">
            <img width="90" height="90" class="product-img" src="https://i.ibb.co/54s4XfL/1.png" alt="">
        </div>

        <div class="col sm-1-1">
            <Text tag="p" size="lg">Tshirt</Text>
            <Text tag="p" size="lg" color="var(--c-darkgray)">Oversize</Text>
        </div>

        <div class="col sm-1-2">
            <div class="quant">
                <Button size="sm full-radius" color="var(--c-darkgray)"><Text size="lg" color="white"> - </Text></Button>
                <Text>1</Text>
                <Button size="sm full-radius" color="var(--c-darkgray)"><Text size="lg" color="white"> + </Text></Button>
            </div>
        </div>

        <div class="col sm-1-2">
            <Text tag="h4" size="xl">54$</Text>
        </div>
    </div>
</div>
</template>

<script>
import Text from '../Texts/Text.vue';
import IconHearth from '../icons/IconHearth.vue';
import Button from '../Buttons/Button.vue';

export default {
    components: { Text, IconHearth, Button }
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