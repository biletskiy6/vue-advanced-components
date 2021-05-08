<script>
export default {
  data() {
    return {
      tag: ""
    };
  },
  model: {
    prop: "tags",
    event: "update"
  },
  props: {
    tags: {
      type: Array,
      default: []
    },
    removeOnBackspace: {
      type: Boolean,
      default: true
    }
  },
  computed: {
    emptyTag() {
      return this.tag.length === 0;
    }
  },
  methods: {
    removeTag(tag) {
      this.$emit(
        "update",
        this.tags.filter(t => t !== tag)
      );
    },
    onInput(newValue) {
      this.tag = newValue;
    },
    addTag() {
      if (!this.emptyTag && !this.tags.includes(this.tag)) {
        // this.tags.push(this.tag);
        this.$emit("update", [...this.tags, this.tag]);
        this.tag = "";
      }
    },
    deleteTag() {
      if (this.emptyTag) {
        // this.tags.pop();
        this.$emit("update", this.tags.slice(0, -1));
      }
    }
  },
  render() {
    return this.$scopedSlots.default({
      tags: this.tags,
      removeButtonHandlers: tag => ({
        click: () => this.removeTag(tag)
      }),
      inputProps: {
        value: this.tag
      },
      inputHandlers: {
        input: e => (this.tag = e.target.value),
        keydown: e => {
          if (e.key === "Enter") {
            this.addTag();
          }
          if (e.key === "Backspace" && this.removeOnBackspace) {
            this.deleteTag();
          }
        }
      }
    });
  }
};
</script>
