<template>
  <div class="user-panel">
    <div class="block">
      <template v-if="userPickedItems && userPickedItems.length">
        <div class="user-panel__picked-items items">
          <div
            v-for="item in userPickedItems"
            :key="item.id"
            class="user-panel__picked-item item"
            @click="clickOnItem(item)"
          >
            {{ item.name }}
          </div>
        </div>
        <span>selected: {{ userPickedItems.length }} / 6</span>
      </template>
      <div v-else class="user-panel__picked-items">Selected items</div>
    </div>
    <div class="block">
      <div class="user-panel__items items">
        <div
          v-for="item in userItems"
          :key="item.id"
          class="user-panel__item item"
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
  name: "UserPanel",
  props: {
    userPickedItems: {
      type: Array,
      default() {
        return [];
      },
    },
    userItems: {
      type: Array,
      default() {
        return [];
      },
    },
  },
  methods: {
    isPicked(item) {
      return this.userPickedItems.some((userItem) => userItem.id === item.id);
    },
    clickOnItem(item) {
      this.$emit("click-on-item", item);
    },
  },
};
</script>

<style scoped></style>
