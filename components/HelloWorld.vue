<script>
export default {
  props: ["tag"],
  render(createElement) {
    return createElement(
      this.tag,
      {
        attrs: {
          class: "btn btn-blue"
        },
        on: {
          click() {
            alert(1);
          }
        }
      },
      this.$slots.default
    );
  }
};
</script>

<style></style>
