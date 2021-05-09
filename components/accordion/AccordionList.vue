<template>
  <div class="accordion-list">
    <slot />
  </div>
</template>

<script>
export default {
  provide() {
    return {
      accordionState: this.accordionState
    };
  },
  data() {
    return {
      accordionState: {
        activeItem: 1
      }
    };
  }
};
</script>

<style></style>
