<template>
    <div>
        <button @click="changeTheme">
            <IconMoon v-if="!theme" width="16" height="16" color="white"/>
            <IconSun v-else width="16" height="16" color="white"/>
        </button>
    </div>
</template>
<script>

import IconSun from '../icons/IconSun.vue';
import IconMoon from '../icons/IconMoon.vue';

export default {
    name: 'ThemeButton',
    components: { IconSun, IconMoon },
    data(){
        return{
            theme: true, // true: darkTheme, false: lightTheme
        }
    },
    created() {
        let initTheme = localStorage.getItem("theme")
        document.documentElement.setAttribute("data-theme", initTheme);
    },
    methods:{
        changeTheme(){
            this.theme = !this.theme
            if(this.theme){
                document.documentElement.setAttribute("data-theme", "dark");
                localStorage.setItem("theme", "dark")
            } else{
                document.documentElement.setAttribute("data-theme", "light");
                localStorage.setItem("theme", "light")
            }
        }
    }
}
</script>
<style scoped>
    button{
        display: flex;
        justify-content: center;
        align-items: center;
        padding: 6px 12px;
        border-radius: 6px;
        background: var(--c-purple);
        color: #fff;
        cursor: pointer;
    }
</style>