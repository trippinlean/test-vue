<template>
  <div id="app">
    <div class="user-panel">
      <div class="block">
        <template v-if="userPickedItems && userPickedItems.length">
          <div class="user-panel__picked-items items">
            <div
              v-for="item in userPickedItems"
              :key="item.id"
              class="user-panel__picked-item item"
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
            @click="toggleItemToUser(item)"
          >
            {{ item.name }}
          </div>
        </div>
      </div>
    </div>
    <div class="store-panel">
      <div class="block">
        <div
          class="store-panel__picked-item"
          :class="{ item: storePickedItem }"
        >
          {{ storePickedItem ? storePickedItem.name : "Store picked item" }}
        </div>
      </div>
      <div class="block">
        <div class="store-panel__items items">
          <div
            v-for="item in storeItems"
            :key="item.id"
            class="store-panel__item item"
            @click="toggleItemToStore(item)"
          >
            {{ item.name }}
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "App",
  data() {
    return {
      userPickedItems: [],
      userItems: [
        {
          id: 1,
          name: "Shoes 1",
        },
        {
          id: 2,
          name: "Shoes 2",
        },
        {
          id: 3,
          name: "Shoes 3",
        },
        {
          id: 4,
          name: "Shoes 4",
        },
        {
          id: 5,
          name: "T-shirt 1",
        },
        {
          id: 6,
          name: "T-shirt 2",
        },
        {
          id: 7,
          name: "T-shirt 3",
        },
        {
          id: 8,
          name: "T-shirt 4",
        },
      ],
      storePickedItem: null,
      storeItems: [
        {
          id: 11,
          name: "Jacket 1",
        },
        {
          id: 12,
          name: "Jacket 2",
        },
        {
          id: 13,
          name: "Jacket 3",
        },
        {
          id: 14,
          name: "Jacket 4",
        },
        {
          id: 15,
          name: "Hoodie 1",
        },
        {
          id: 16,
          name: "Hoodie 2",
        },
        {
          id: 17,
          name: "Hoodie 3",
        },
        {
          id: 18,
          name: "Hoodie 4",
        },
      ],
    };
  },
  methods: {
    toggleItemToUser(candidate) {
      const itemIndex = this.userPickedItems.findIndex(
        (item) => item.id === candidate.id
      );
      if (itemIndex !== -1) {
        this.userPickedItems.splice(itemIndex, 1);
      } else {
        if (this.userPickedItems.length <= 5)
          this.userPickedItems.push(candidate);
      }
    },
    toggleItemToStore(item) {
      if (this.storePickedItem?.id === item.id) {
        this.storePickedItem = null;
      } else {
        this.storePickedItem = item;
      }
    },
  },
};
</script>

<style lang="scss">
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
  display: flex;
  justify-content: space-evenly;
  min-height: 414px;
}
.items {
  display: flex;
  flex-wrap: wrap;
  gap: 10px;
  max-width: 302px;
}
.item {
  width: 60px;
  height: 60px;
  background: #3ae6ca;
  border-radius: 4px;
  display: flex;
  justify-content: center;
  align-items: center;
  padding: 4px;
  &--active {
    border: 1px solid gold;
  }
}
.block {
  border: 1px solid black;
  padding: 14px;
  margin-bottom: 16px;
}
.user-panel {
  display: flex;
  flex-direction: column;
  justify-content: space-between;
  &__picked-items {
    margin-bottom: 12px;
  }
}
.store-panel {
  display: flex;
  flex-direction: column;
  justify-content: space-between;
  align-items: center;
}
</style>
