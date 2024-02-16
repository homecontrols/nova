<script setup>
  import Logo from "./Logo.vue";
  import IconButton from "./IconButton.vue";
  import Avatar from "./Avatar.vue";

  const collapsed = ref(true);
</script>

<template>
  <nav
    :class="{
      collapsed: collapsed === true,
    }">
    <div class="logo">
      <Logo @click="() => (collapsed = false)" />
      <div class="version">
        <p class="bold">Homecontrols</p>
        <span>version 0.1.0</span>
      </div>
      <IconButton
        class="collapse_button"
        icon="keyboard_double_arrow_left"
        @click="() => (collapsed = true)" />
    </div>
    <div class="links">
      <IconButton icon="home" label="Dashboard" />
      <IconButton icon="home_iot_device" label="Devices" />
      <IconButton icon="bolt" label="Energy" />
      <IconButton icon="wifi" label="Network" />
    </div>
    <div class="bottom">
      <Avatar />
      <IconButton src="/icons/terminal.svg" label="Terminal & Logs" />
      <IconButton icon="settings" label="Settigns" />
    </div>
  </nav>
</template>

<style scoped>
  nav {
    position: absolute;
    top: 0;
    left: 0;
    background: var(--surface);
    width: 4rem;
    height: 100vh;
    padding: 0.5rem;
    overflow: hidden;

    display: flex;
    flex-direction: column;
    gap: 1rem;
    transition: width 0.3s ease;

    & > div {
      width: 100%;
    }

    &:not(.collapsed) {
      width: 20rem;
    }
  }

  .logo {
    width: 3rem;
    height: 3rem;
    display: flex;
    gap: 1rem;

    & .version {
      display: flex;
      flex-direction: column;
      justify-content: center;
      width: 100%;

      & :nth-child(1) {
        margin-bottom: -0.5rem;
      }

      & span {
        font-size: 0.75rem;
      }
    }

    & .collapse_button {
      flex-shrink: 0;
    }
  }

  .links {
    height: 100%;
  }

  .links,
  .bottom {
    display: flex;
    flex-direction: column;
    gap: 0.5rem;
  }
</style>
