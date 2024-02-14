<script setup>
  import Logo from "./Logo.vue";
  import IconButton from "./IconButton.vue";
  import Avatar from "./Avatar.vue";
</script>

<template>
  <nav>
    <div class="logo">
      <Logo />
    </div>
    <div class="links">
      <IconButton icon="home" />
      <IconButton icon="home_iot_device" />
      <IconButton icon="bolt" />
      <IconButton icon="wifi" />
    </div>
    <div class="bottom">
      <Avatar />
      <IconButton src="/icons/terminal.svg" />
      <IconButton icon="settings" />
    </div>
  </nav>
</template>

<style scoped>
  nav {
    background: var(--surface);
    width: 4rem;
    height: 100vh;
    padding: 0.5rem;

    display: flex;
    flex-direction: column;
    align-items: center;
    gap: 1rem;

    & > div {
      width: 100%;
    }
  }

  .logo {
    width: 3rem;
    height: 3rem;
  }

  .links {
    height: 100%;
  }

  .links,
  .bottom {
    display: flex;
    flex-direction: column;
    align-items: center;
    gap: 0.5rem;
  }
</style>
