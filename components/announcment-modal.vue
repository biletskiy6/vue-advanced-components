<template>
  <app-modal :show="show" @close="handleClose">
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
  </app-modal>
</template>

<script>
  import AppModal from './app-modal'
  export default {
    components: {
      AppModal
    },
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
    methods: {
      handleClose() {
        this.$emit('close')
      }
    },
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
