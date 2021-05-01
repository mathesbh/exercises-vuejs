<template>
  <section>
    <Search :onSearch="handleSearchProducts"/>
    <div class="box">
      <div v-if="listedProducts.length > 0">
        <div v-for="(item, index) in listedProducts" :key="index">
          <ProductItem :product="item" />
        </div>
      </div>
      <div v-else>
        <div v-for="(item, index) in products" :key="index">
          <ProductItem :product="item" />
        </div>
      </div>
    </div>
    <p>{{ totalProducts }}</p>
    <router-link to="/">Ir para cadastro de produtos</router-link>
  </section>
</template>

<script>
import ProductItem from "./ProductItem";
import Search from './Search';

export default {
  name: "ProductList",
  components: {
    ProductItem,
    Search,
  },
  props: {
  },
  data(){
    return{
      products: this.$store.getters.getProducts,
      listedProducts: [],
    }
  },
  methods: {
    handleSearchProducts(text){
      const results = this.products.filter((e) => e.name.startsWith(text));
      if(results.length > 0){
        this.listedProducts = results;
      } else {
        this.listedProducts = this.products;
      }
    }
  },
  computed: {
    totalProducts: function(){
      const products = this.$store.state.products.length;
      const listedProducts = this.listedProducts.length;
      const total = listedProducts > 0 ? listedProducts : products;
      return total > 1 || total === 0 ? `Total: ${total} produtos` : `Total: ${total} produto`;
    },
  },
};
</script>

<style scoped>
section {
  width: 220px;
}

.box div{
  background-color: rgb(219, 219, 219);
}

section p{
  text-align: center;
}

div {
  padding: 10px 10px 5px 10px;
}

a{
  position: absolute;
  margin-top: 25px;
  color: rgb(50, 170, 50);
  text-decoration: none;
  font-size: 1.2rem;
}
</style>