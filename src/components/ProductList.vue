<template>
  <section>
    <div v-for="(item, index) in products" :key="index">
      <ProductItem :product="item" />
    </div>
    <p>{{ totalProducts }}</p>
  </section>
</template>

<script>
import ProductItem from "./ProductItem";

export default {
  name: "ProductList",
  components: {
    ProductItem,
  },
  props: {
    products: Array
  },
  data(){
    return{

    }
  },
  computed: {
    totalProducts: function(){
      const total = this.products.length;

      return `Total: ${total} produtos`;
    },
  },
};
</script>

<style scoped>
section {
  background-color: rgb(219, 219, 219);
  padding-bottom: 5px;
}

section p{
  float: right;
}
div {
  
  padding: 10px 10px 5px 10px;
}
</style>