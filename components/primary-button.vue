<template>
  <button class="btn btn-blue">
    <slot name="icon"></slot>
    <slot name="text"></slot>
  </button>
</template>

<script>
export default {
  name: "primary-button"
}
</script>
