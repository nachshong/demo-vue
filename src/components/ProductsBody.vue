<script lang="ts">
    import MyProduct from "./MyProduct.vue";
    import type { Product } from '../types/product'
    
    export default {
        components: {
            MyProduct
        },
        props: {
            list: {} as Product[]
        }
    }
</script>

    <template>
      <section class="products">
        <template v-for="p in list">
            <MyProduct :item="p" />
        </template>
      </section>
    </template>
    
    <style scoped>
    .products {
      display: flex;
      flex-wrap: wrap;
    }
    @media (max-width: 920px) {
      .products .product-card:first-child,
      .products .product-card:nth-child(2) {
        flex: 2 46%;
      }
    }
    </style>
    