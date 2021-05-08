<template>
  <div class="tag-input">
    <span v-for="tag in tags" :key="tag" class="tag-input-tag">
      <span>{{ tag }} </span>
      <button class="tag-input-remove">&times;</button>
    </span>
    <input
      v-model="tag"
      class="tag-input-text"
      placeholder="Add Tag"
      type="text"
      @keydown.delete="handleDelete"
      @keydown.enter="handleCreate"
    />
  </div>
</template>

<script>
export default {
  model: {
    prop: "tags",
    event: "update"
  },
  props: ["tags"],
  data() {
    return {
      tag: ""
    };
  },
  computed: {
    emptyTag() {
      return this.tag.length === 0;
    }
  },
  methods: {
    handleCreate() {
      if (!this.emptyTag && !this.tags.includes(this.tag)) {
        // this.tags.push(this.tag);
        this.$emit("update", [...this.tags, this.tag]);
        this.tag = "";
      }
    },
    handleDelete() {
      if (this.emptyTag) {
        // this.tags.pop();
        this.$emit("update", this.tags.slice(0, -1));
      }
    }
  }
};
</script>

<style></style>
