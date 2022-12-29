<template>
  <div class="app_container">
    <HeaderVue @handleSend="handleSearch" />
    <div class="products">
      <SingleProduct v-if="productInfo" :productInfo="productInfo" @comment="handleComment" />
      <ProductItem v-else :products="products" @productId="singlePRoduct" />
    </div>
  </div>
</template>
<script>
import product from "./products.json"
import HeaderVue from "./components/Header.vue";
import ProductItem from "./components/ProductItem.vue";
import SingleProduct from "./components/SingleProduct.vue";
export default {
  data() {
    return {
      products: JSON.parse(JSON.stringify(product)),
      productInfo: false,
    }
  },
  components: {
    HeaderVue,
    ProductItem,
    SingleProduct
  },
  methods: {
    handleSearch(productName) {
      this.products = JSON.parse(JSON.stringify(product)).filter(item => item.name.toLowerCase().includes(productName.toLowerCase()))
    },
    singlePRoduct(itemId) {
      this.productInfo = JSON.parse(JSON.stringify(this.products)).filter(item => item.id === itemId)
    },
    handleComment(item) {
      this.products[this.productInfo[0].id].comments.push({ id: Date.now(), comment: item.toString() })
      localStorage.setItem("data")
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