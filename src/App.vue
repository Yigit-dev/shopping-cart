<template>
    <Layout>
        <router-view />
    </Layout>
</template>
<script>
import HomeView from './views/HomeView.vue';
import Layout from './layout/index.vue';
export default {
    name: "App",
    components: { HomeView, Layout }
}
</script>