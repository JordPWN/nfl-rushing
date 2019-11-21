<template>
  <button class="button" @click="sendClick">
    <slot />
  </button>
</template>

<script>
export default {
  name: "s-button",
  methods: {
    sendClick() {
      this.$emit("click")
    }
  }
}
</script>

<style lang="scss">
.button {
  display: flex;
  flex-direction: column;
  font-size: 1em;
  max-width: 10em;
  padding: 1em;
  background-color: var(--brand-accent);
  color: var(--white);
  border-radius: 0.3em;
  border: none;
  outline: none;
  cursor: pointer;
  font-weight: bold;
  &:hover,
  &:active {
    background-color: var(--brand-hover);
  }
}
</style>