<template>
  <div class="container">
    <ProductForm :onAddProduct="handleOnAddProduct"/>
    <div class="box">
      <Search />    
      <ProductList :products="products"/>
    </div>
  </div>
</template>

<script>
import ProductForm from './components/ProductForm';
import ProductList from './components/ProductList';
import Search from './components/Search';

export default {
  name: 'App',
  components: {
    ProductForm,
    ProductList,
    Search,
  },
  data(){
    return{
      products: [
        {
          name: 'Iphone 12',
          price: '10000.00',
          category: 'Smartphone',
        },
        {
          name: 'Samsung Galaxy',
          price: '5000.00',
          category: 'Smartphone',
        },
      ]
    }
  },
  methods: {
    handleOnAddProduct(product){
      this.products = this.products.concat(product);
    }
  }
}
</script>

<style scoped>
  .container{
    display: flex;
    justify-content: space-evenly;
  }
</style>
