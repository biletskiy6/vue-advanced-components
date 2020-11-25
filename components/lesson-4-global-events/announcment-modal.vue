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
  name: "announcment-modal",
  props: {
    show: {
      type: Boolean,
      default: false,
      required: true
    },
    preventBackgroundScrolling: {
      type: Boolean,
      default: true
    }
  },
  mounted() {
    this.escapeHandler = e => {
      if (e.key === "Escape" && this.show) {
        this.handleClose();
      }
    };
    document.addEventListener("keydown", this.escapeHandler);
  },
  destroyed() {
    document.removeEventListener("keydown", this.escapeHandler);
  },
  watch: {
    show: {
      handler: function(show) {
        if (show) {
          this.preventBackgroundScrolling &&
            document.body.style.setProperty("overflow", "hidden");
        } else {
          this.preventBackgroundScrolling &&
            document.body.style.removeProperty("overflow", "hidden");
        }
      },
      immediate: true
    }
  },
  methods: {
    handleClose() {
      this.$emit("close");
    }
  }
};
</script>

<style>
.modal {
  border: 1px solid blue;
}
.modal:focus {
  outline: 2px solid red;
}
</style>
