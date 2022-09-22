<script lang="ts">
import { defineComponent } from "vue";
import type { Product } from '../types/product';
import JsonProducts from '../assets/products.json';

import ProductsFilters from '../components/ProductsFilters.vue';
import ProductsBody from '../components/ProductsBody.vue';

export default defineComponent({
  components: {
    ProductsBody,
    ProductsFilters
  },
  data() {
    return {
      allProducts: JsonProducts,
      filters: {
        category: ''
      }
    }
  },
  computed: {
    categories(): string[] {
      return [...new Set<string>(this.allProducts.map((p: Product) => p.category))];
    },
    products(): Product[] {
      return this.allProducts.filter((p) => !this.filters.category || p.category == this.filters.category)
    }
  },
  methods: {
    filterByCategory(c: string) {
      this.filters.category = c;
    }
  },
})
</script>
  
<template>
  <div>
    <ProductsFilters :categories="categories" @filter="filterByCategory" />
  </div>
  <div>
    <ProductsBody :list="products" />
  </div>
</template>
  
<style scoped>
header {
  line-height: 1.5;
  max-height: 100vh;
}

.logo {
  display: block;
  margin: 0 auto 2rem;
}

nav {
  width: 100%;
  font-size: 12px;
  text-align: center;
  margin-top: 2rem;
}

nav a.router-link-exact-active {
  color: var(--color-text);
}

nav a.router-link-exact-active:hover {
  background-color: transparent;
}

nav a {
  display: inline-block;
  padding: 0 1rem;
  border-left: 1px solid var(--color-border);
}

nav a:first-of-type {
  border: 0;
}

@media (min-width: 1024px) {
  header {
    display: flex;
    place-items: center;
    padding-right: calc(var(--section-gap) / 2);
  }

  .logo {
    margin: 0 2rem 0 0;
  }

  header .wrapper {
    display: flex;
    place-items: flex-start;
    flex-wrap: wrap;
  }

  nav {
    text-align: left;
    margin-left: -1rem;
    font-size: 1rem;

    padding: 1rem 0;
    margin-top: 1rem;
  }
}
</style>
  