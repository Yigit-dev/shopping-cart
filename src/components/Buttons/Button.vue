<template>
    <button :style="{ 'background-color': color }" :class="size" :disabled="disabled">
      <slot />
    </button>
</template>

<script>
export default {
    name: 'CustomButton',
    props: {
        color: {
            types: String,
            default: "transparent",
        },
        size: {
            type: String,
            default: "normal",
            validator: (value) =>
                ["lg", "md", "sm", "xs", "xxs", "xs-radii"].indexOf(value) !== -1,
        },
        radius: {
          type: String,
          default: '0'
        },
        disabled: {
            type: Boolean,
            default: false
        }
  },
}
</script>
<style scoped>
    button{
        display: flex;
        justify-content: center;
        align-items: center;
        border: none;
        border-radius: 6px;
        transition: 200ms all;
        border: 1px solid transparent;
    }
    button:hover{
        transform: scale(1.03);
        border: 1px solid gray;
        transition: 200ms all;
    }
    .lg{
        padding: 18px;
    }
    .md {
        padding: 14px;
    }
    .sm {
        padding: 12px;
    }
    .xs {
        padding: 11px;
    }
    .xxs {
        padding: 1px 8px;
    }
    .full-radius {
        border-radius: 100%;
    }
    .sm.full-radius{
        width: 28px;
        height: 28px;
    }
</style>