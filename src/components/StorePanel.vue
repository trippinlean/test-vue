<template>
  <div class="store-panel">
    <div class="block">
      <div class="store-panel__picked-item" :class="{ item: storePickedItem }">
        {{ storePickedItem ? storePickedItem.name : "Store picked item" }}
      </div>
    </div>
    <div class="block">
      <div class="store-panel__items items">
        <div
          v-for="item in storeItems"
          :key="item.id"
          class="store-panel__item item"
          :class="{ 'item--active': isPicked(item) }"
          @click="clickOnItem(item)"
        >
          {{ item.name }}
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "StorePanel",
  props: {
    storePickedItem: {
      type: Object,
      default() {
        return {};
      },
    },
    storeItems: {
      type: Array,
      default() {
        return [];
      },
    },
  },
  methods: {
    isPicked(item) {
      return this.storePickedItem?.id === item.id;
    },
    clickOnItem(item) {
      this.$emit("click-on-item", item);
    },
  },
};
</script>

<style scoped></style>
