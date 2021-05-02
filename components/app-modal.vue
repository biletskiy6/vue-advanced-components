<template>
  <portal to="modals" v-if="show">
  <div class="modal-backdrop" v-show="show">
    <div ref="modal" class="modal" tabindex="0">
      <slot />
    </div>
  </div>
  </portal>
</template>

<script>
export default {
  name: "AppModal",
  props: {
    show: {
      type: Boolean,
      default: false
    },
    preventBackgroundScrolling: {
      type: Boolean,
      default: true
    }
  },
  mounted() {
    const eventHandler = (event) => {
      if (this.show && event.key === 'Escape') {
        this.handleClose()
      }
    }
    window.addEventListener('keydown', eventHandler)
    this.$once('hook:destroyed', () => {
      window.removeEventListener('keydown', eventHandler)
    })
  },
  methods: {
    handleClose() {
      this.$emit('close')
    }
  },
  watch: {
    show: {
      handler(isOpen) {
        if(!process.client) return
        isOpen
          ? this.preventBackgroundScrolling && document.body.style.setProperty('overflow', 'hidden')
          : this.preventBackgroundScrolling && document.body.style.removeProperty('overflow')
      },
      immediate: true
    }
  }
}
</script>
