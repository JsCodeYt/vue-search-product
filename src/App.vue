<template>
  <div class="app_container">
    <HeaderVue @handleSend="handleSearch" />
    <div class="products">
      <ProductItem :products="products" />
    </div>
  </div>
</template>
<script>
import product from "./products.json"
import HeaderVue from "./components/Header.vue";
import ProductItem from "./components/ProductItem.vue";
export default {
  data() {
    return {
      products: JSON.parse(JSON.stringify(product))
    }
  },
  components: {
    HeaderVue,
    ProductItem
  },
  methods: {
    handleSearch(productName) {
      this.products = JSON.parse(JSON.stringify(product)).filter(item => item.name.toLowerCase().includes(productName))
    }
  }
}
</script>
<style lang="scss">
.app_container {
  display: flex;
  align-items: center;
  justify-content: center;
  flex-direction: column;
  gap: 1rem;
  font-family: "Poppins", sans-serif;

  .products {
    display: flex;
    align-items: center;
    flex-wrap: wrap;
    gap: 1rem;
    width: 80%;
  }
}
</style>