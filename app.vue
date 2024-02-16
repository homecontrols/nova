<template>
  <div class="root">
    <NuxtPage />
  </div>
</template>

<style>
  :root {
    --background: #1f2223;
    --surface: #181a1b;
    --hover: #313435;
    --active: #3e4142;
    --text: #c7c7c7;
    --accent: #5566b8; /* This should be editable by user */
    --accent-dim: rgba(85, 102, 184, 0.25);
  }

  * {
    box-sizing: border-box;
  }

  html,
  body {
    margin: 0;
    padding: 0;
    background: var(--background);
    color: var(--text);
    font-family: "Poppins", sans-serif;
    height: 100%;
    width: 100%;
    overflow-x: hidden;
  }

  h1,
  h2,
  h3,
  h4,
  h5,
  h6,
  p {
    margin: 0;
  }

  p.bold {
    font-weight: 700;
  }

  main {
    margin-left: 4rem;
  }
</style>

<style scoped>
  div.root {
    width: 100vw;
    min-height: 100vh;
    overflow-x: hidden;
    display: flex;
  }
</style>
