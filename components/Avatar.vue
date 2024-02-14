<script setup lang="ts">
  const props = withDefaults(
    defineProps<{
      src?: string;
    }>(),
    {
      src: "",
    }
  );
</script>

<template>
  <div class="avatar">
    <div class="icon"></div>
  </div>
</template>

<style scoped>
  .avatar {
    width: 3rem;
    height: 3rem;
    padding: 0.25rem;
  }

  .icon {
    width: 2.5rem;
    height: 2.5rem;
    border-radius: 1.5rem;
    background: var(--accent);
  }
</style>
