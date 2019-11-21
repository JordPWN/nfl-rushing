<template>
  <div id="app">
    <router-view />
  </div>
</template>

<style lang="scss">
:root {
  --black: black;
  --white: #f9f9f9;
  --dark-grey: #3a3d40;
  --dark-gray: #3a3d40;
  --nav-accent: #1e1f21;
  --brand-accent: #0078fd;
  --brand-hover:#3290fc;
}
html,
body {
  padding: 0;
  margin: 0;
  color: var(--white);
  background-color: var(--black);
}
input {
  background-color: #3a3d40;
  font-size: 1em;
  color: var(--white);
  border: none;
  outline: none;
  height: 4em;
  padding-left: 1em;
  border-radius: 0.3em;
}
#app {
  font-family: "Avenir", Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: var(--white);
}
</style>
