<script lang="ts">
    import type { Product } from "../types/product";
    export default {

        props: {
            item: {} as Product
        }

    }
</script>
<template>
  <div class="product-card">
    <div class="product-image">
     <img :src="item.image"
      />
    </div>
    <div class="product-info">
      <h5>{{item.title}}</h5>
      <h6>${{item.price}}</h6>
    </div>
  </div>
</template>

<style scoped>
.product-card {
  display: flex;
  flex-direction: column;

  padding: 2%;
  flex: 1 16%;

  background-color: #fff;
  box-shadow: 0px 0px 1px 0px rgba(0, 0, 0, 0.25);
}

.product-image img {
  width: 100%;
}

.product-info {
  margin-top: auto;
  padding-top: 20px;
  text-align: center;
}
@media (max-width: 920px) {
  .product-card {
    flex: 1 21%;
  }

  .products .product-card:first-child,
  .products .product-card:nth-child(2) {
    flex: 2 46%;
  }
}

@media (max-width: 600px) {
  .product-card {
    flex: 1 46%;
  }
}
</style>
