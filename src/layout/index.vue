<template>
<div>
    <Navigation />
    <div class="container">
      <main class="pageAnimation">
        <slot />
      </main>
    </div>
    <Footer />
</div>
</template>
  
<script>
import Navigation from "./Navigation.vue";
import Footer from "./Footer.vue";

export default {
    components: {Navigation,Footer},
};
</script>
  
<style scoped>
  .container {
    position: relative;
    background: var(--theme-bg);
    transition: background-color 0.5s;
    width: 100%;
    min-height: 100vh;
    padding: 4vw;
    overflow: hidden;
  }
  main{
    display: flex;
    justify-content: center;
    flex-direction: column;
  }
</style>
  