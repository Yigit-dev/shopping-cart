<template>
    <nav>
        <div class="wrap xl-flexbox xl-between sm-center">
            <div class="col sm-1-1">
                <h1>LOGO</h1>
            </div>
            <div class="col sm-1-1">
                <ul>
                    <li><router-link to="/" class="navigation-link" active-class="is-active"><Text size="md" fontWeight="700">Home</Text></router-link></li>
                    <li><router-link to="/shopping-cart" class="navigation-link" active-class="is-active"><Text size="md" fontWeight="700">Shopping Cart</Text></router-link></li>
                    <li><ThemeButton /></li>
                </ul>
            </div>
        </div>
    </nav>
</template>
<script>
import ThemeButton from "@/components/Buttons/ThemeButton.vue"
import Text from "../components/Texts/Text.vue";
export default {
    name: "Navigation",
    components: { ThemeButton, Text }
}
</script>
<style scoped>
nav{
    background: var(--nav-bg);
    padding: 16px 64px;
}
nav ul{
    display: flex;
    align-items: center;
}
nav ul li{
    list-style: none;
}
.navigation-link{
    text-decoration: none;
}
.navigation-link span{
    margin: 0 24px;
    transition: 200ms all;
    padding: 6px 12px;
    border-radius: 6px;
}
.navigation-link span:hover{
    background: #fff;
    color: #000!important;
    transition: 200ms all;
}
@media screen and (max-width: 768px) {
    nav{
        padding: 16px 0;
    }
    nav ul{
        justify-content: center;
    }
    .navigation-link span{
        margin: 0 16px;
    }
}
</style>