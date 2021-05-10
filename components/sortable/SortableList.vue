<script>
function move(items, oldIndex, newIndex) {
  const itemRemovedArray = [
    ...items.slice(0, oldIndex),
    ...items.slice(oldIndex + 1, items.length)
  ];

  return [
    ...itemRemovedArray.slice(0, newIndex),
    items[oldIndex],
    ...itemRemovedArray.slice(newIndex, itemRemovedArray.length)
  ];
}

export default {
  mounted() {
    this.initDraggable();
  },
  props: {
    sortableListItemClass: {
      type: String,
      default: "sortable-list-item"
    },
    sortableListHandleClass: {
      type: String,
      default: "sortable-list-item"
    },
    value: {
      type: Array,
      default: []
    }
  },
  provide() {
    return {
      sortableListItemClass: this.sortableListItemClass,
      sortableListHandleClass: this.sortableListHandleClass
    };
  },
  methods: {
    initDraggable() {
      if (process.client) {
        const { Sortable } = require("@shopify/draggable");
        new Sortable(this.$el, {
          draggable: `.${this.sortableListItemClass}`,
          handle: `.${this.sortableListHandleClass}`,
          mirror: {
            constrainDimensions: true
          }
        }).on("sortable:stop", ({ oldIndex, newIndex }) => {
          this.$emit("input", move(this.value, oldIndex, newIndex));
          // console.log("drag:stop", el);
        });
      }
    }
  },
  render() {
    return this.$slots.default[0];
  }
};
</script>
