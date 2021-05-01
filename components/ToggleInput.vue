<template>
 <span
   class="toggle"
   role="checkbox"
   tabindex="0"
   @click="toggle"
   :aria-checked="toggled.toString()"
   @keydown.space.prevent="toggle"
 ></span>
</template>

<script>
export default {
  name: "ToggleInput",
  model: {
    prop: 'toggled',
    event: 'toggle'
  },
  props: {
    toggled: {
      type: Boolean,
      default: false
    }
  },
  methods: {
    toggle() {
      this.$emit('toggle', !this.toggled)
    }
  }
}
</script>
