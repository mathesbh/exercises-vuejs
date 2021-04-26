<template>
  <div class="container">
    <div class="box">
      <h4>{{ product.name }}</h4>
      <p>R${{ product.price }}</p>
      <p>{{ product.category }}</p>
    </div>
  </div>
</template>

<script>
export default {
  name: 'ProductItem',
  props: {
    product: Object,
  },

};
</script>

<style scoped>

.box{
  border: 3px solid white;
  text-align: center;
  margin: 5px 0;
  padding: 10px;
}
</style>