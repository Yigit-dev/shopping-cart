<template>
    <component :is="tag" :class="size" :style="{ 'color': color, 'fontWeight': fontWeight }">
      <slot />
    </component>
  </template>
  <script>
  export default {
    name: "Text",
    props: {
      tag: {
        types: String,
        default: "span",
      },
      size: {
        type: String,
        default: "normal",
        validator: (value) => ["xxl", "xl", "lg", "md", "sm"].indexOf(value) !== -1,
      },
      color: {
        types: String,
        default: "var(--c-text)",
      },
      fontWeight: {
        type: String,
      }
    },
  };
  </script>
  <style scoped>
  .xxl {
    font-size: 28px;
  }
  .xl {
    font-size: 24px;
  }
  .lg {
    font-size: 18px;
  }
  .md {
    font-size: 15px;
  }
  .sm {
    font-size: 13px;
  }
  </style>
  