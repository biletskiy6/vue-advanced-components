<script>
export default {
  name: "ContactList",
  data() {
    return {
      json: null,
      loading: true
    };
  },
  created() {
    fetch("/contacts.json")
      .then(response => response.json())
      .then(json => {
        setTimeout(() => {
          this.json = json;
          this.loading = false;
        }, 2000);
      });
  },
  render(createElement) {
    return this.$scopedSlots.default({
      contacts: this.json,
      loading: this.loading
    });
  }
};
</script>
