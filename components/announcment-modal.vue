<template>
  <div class="modal-backdrop" v-show="show">
    <div ref="modal" class="modal" tabindex="0">
      <h1 class="text-center text-2xl font-bold mb-4">Here is a title</h1>
      <p class="text-center mb-6">
        Lorem ipsum dolor sit amet, consectetur adipisicing elit. Aut cupiditate
        dolore eligendi exercitationem, labore libero obcaecati provident sed
        veniam vero. Labore praesentium, soluta. Ab autem corporis cum mollitia
        quam, similique?
      </p>
      <div class="text-center">
        <button @click="handleClose" class="btn btn-blue" type="button">
          Dismiss
        </button>
      </div>
    </div>
  </div>
</template>

<script>
  export default {
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
          isOpen
            ? this.preventBackgroundScrolling && document.body.style.setProperty('overflow', 'hidden')
            : this.preventBackgroundScrolling && document.body.style.removeProperty('overflow')
        },
        immediate: true
      }
    }
  }
</script>
<style>
.modal {
  border: 1px solid blue;
}
.modal:focus {
  outline: 2px solid red;
}
</style>
