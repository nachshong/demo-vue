<script  lang="ts">
import { defineComponent } from "vue";

export default defineComponent({

  props: {
    categories: Array<string>
  },

  data() {
    return {
      category: ''
    }
  },

  watch: {
    category(newVal: string, oldVal: string) {
      if (newVal != oldVal) {
        this.$emit('filter', newVal);
        console.log(newVal || 'All');
      }
    }
  }

});
</script>

<template>
  <nav class="product-filter">
    <h1>Jackets</h1>

    <div class="sort">
      <div class="collection-sort">
        <label>Filter by:</label>
        <select v-model="category">
          <option value="">All</option>
          <option v-for="c in categories">{{c}}</option>
        </select>
      </div>

      <div class="collection-sort">
        <label>Sort by:</label>
        <select>
          <option value="/">Featured</option>
          <option value="/">Best Selling</option>
          <option value="/">Alphabetically, A-Z</option>
          <option value="/">Alphabetically, Z-A</option>
          <option value="/">Price, low to high</option>
          <option value="/">Price, high to low</option>
          <option value="/">Date, new to old</option>
          <option value="/">Date, old to new</option>
        </select>
      </div>
    </div>
  </nav>
</template>

<style scoped>
/* Product Layout */

.product-filter {
  display: flex;
  padding: 30px 0;
}

.sort {
  display: flex;
  align-self: flex-end;
}

.collection-sort {
  display: flex;
  flex-direction: column;
}

.collection-sort:first-child {
  padding-right: 20px;
}

@media (max-width: 480px) {
  .product-filter {
    flex-direction: column;
  }

  .sort {
    align-self: flex-start;
  }
}
</style>
