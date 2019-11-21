<template>
  <div class="page-body">
    <slot />
  </div>
</template>

<script>
export default {
  name: "page-body"
};
</script>

<style lang="scss">
.page-body {
  display: flex;
  flex-direction: column;
  width: 100vw;
  min-height: 100vh;
}
</style>