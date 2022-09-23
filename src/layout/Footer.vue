<template lang="">
    <footer>
        <a href="https://www.yigitcakmak.com"><small>copyright Yigit Cakmak</small></a>
    </footer>
</template>
<script>
export default {
    name: 'Footer'
}
</script>
<style scoped>
    footer {
        background: var(--theme-bg);
        display: flex;
        justify-content: center;
        align-items: center;
        border-top: 1px solid #FFD700;
        padding: 16px 0;
    }
    footer a{
        text-decoration: none;
        color: var(--c-text);
        font-size: 18px;
    }
    footer a:hover{
        text-decoration: underline;
    }
</style>