<script setup lang="ts">
  import type { Ref, ComputedRef } from "vue";
  import { watchEffect, ref } from "vue";
  import Icon from "./Icon.vue";

  const props = withDefaults(
    defineProps<{
      icon?: string;
      src?: string;
      active?: boolean | Ref | ComputedRef;
      hover?: boolean | string;
    }>(),
    {
      icon: "menu",
      src: "",
      active: false,
      hover: true,
    }
  );

  const iconProps = {
    icon: props.icon,
    src: props.src,
  };

  let active = ref("");
  let hover = ref("var(--hover)");

  watchEffect(() => {
    if (props.active) {
      active.value = "var(--active)";
      hover.value = "var(--active)";
    } else {
      active.value = "";
      hover.value =
        props.hover === true
          ? "var(--hover)"
          : typeof props.hover === "string"
          ? props.hover
          : "";
    }
  });
</script>

<template>
  <div class="button">
    <Icon v-bind="iconProps" />
  </div>
</template>

<style scoped>
  .button {
    width: 3rem;
    height: 3rem;
    display: flex;
    align-items: center;
    justify-content: center;
    border-radius: 0.5rem;
    background: v-bind("active");
    transition: background 0.3s ease;
    cursor: pointer;
  }

  .button:hover {
    background: v-bind("hover");
  }
</style>
