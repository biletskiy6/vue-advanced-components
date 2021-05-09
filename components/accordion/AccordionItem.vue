<template>
  <div class="accordion-item">
    <div @click="toggle" class="accordion-item-header">
      {{ itemId }}
      <slot name="header"></slot>
    </div>
    <div class="accordion-item-body" v-if="isOpen">
      <slot name="content"></slot>
    </div>
  </div>
</template>

<script>
export default {
  inject: ["accordionState"],
  computed: {
    currentItem() {
      return this.accordionState.activeItem;
    },
    isOpen() {
      return this.currentItem === this.itemId;
    }
  },
  props: ["itemId"],
  methods: {
    toggle() {
      this.accordionState.activeItem =
        this.currentItem === this.itemId ? null : this.itemId;
    }
  }
};
</script>

<style></style>
