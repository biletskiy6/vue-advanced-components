<template>
  <renderless-tag-input
    :tags="tags"
    @update="
      newTags => {
        $emit('update', newTags);
      }
    "
    :remove-on-backspace="true"
  >
    <div
      slot-scope="{ tags, removeButtonHandlers, inputProps, inputHandlers }"
      class="tag-input"
    >
      <span v-for="tag in tags" :key="tag" class="tag-input-tag">
        <span>{{ tag }} </span>
        <button v-on="removeButtonHandlers(tag)" class="tag-input-remove">
          &times;
        </button>
      </span>
      <input
        v-bind="inputProps"
        v-on="inputHandlers"
        class="tag-input-text"
        placeholder="Add Tag"
        type="text"
      />
    </div>
  </renderless-tag-input>
</template>

<script>
import RenderlessTagInput from "@/components/RenderlessTagInput";
export default {
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
  components: {
    RenderlessTagInput
  }
};
</script>

<style></style>
