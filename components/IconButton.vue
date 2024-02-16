<script setup lang="ts">
  import type { Ref, ComputedRef } from "vue";
  import { watchEffect, ref } from "vue";
  import Icon from "./Icon.vue";

  const props = withDefaults(
    defineProps<{
      icon?: string;
      label?: string;
      src?: string;
      active?: boolean | Ref | ComputedRef;
      hover?: boolean | string;
    }>(),
    {
      icon: "menu",
      label: "",
      src: "",
      active: false,
      hover: true,
    }
  );

  const iconProps = {
    icon: props.icon,
    src: props.src,
    width: props.label !== "" ? "100%" : "3rem",
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
  <div class="icon_button">
    <div class="button">
      <Icon v-bind="iconProps" />
    </div>
    <p>{{ props.label }}</p>
  </div>
</template>

<style scoped>
  .icon_button {
    display: flex;
    align-items: center;
    height: 3rem;
    width: v-bind("iconProps.width");
    gap: 1rem;
    overflow: hidden;

    border-radius: 0.5rem;
    background: v-bind("active");
    transition: background 0.3s ease;
    cursor: pointer;

    &:hover {
      background: v-bind("hover");
    }
  }
  .button {
    width: 3rem;
    height: 3rem;
    flex-shrink: 0;
    display: flex;
    align-items: center;
    justify-content: center;
  }

  p {
    font-weight: 700;
    white-space: nowrap;
  }
</style>
