<template>
  <div>
    <form @submit.prevent="onFormSubmit">
      <p>Cadastro de Produtos:</p>
      <input type="text" placeholder="Nome" v-model="name">
      <input type="number" placeholder="Preço" v-model="price">
      <input type="text" placeholder="Categoria" v-model="category">
      <input type="submit" value="Cadastrar">
    </form>
  </div>
</template>

<script>
export default {
  name: 'ProductForm',
  data(){
    return{
      name: '',
      price: '',
      category: '',
    }
  },
  props: {
    onAddProduct: Function,
  },
  methods: {
    onFormSubmit(){
      const product = {
        name: this.name,
        price: this.price,
        category: this.category,
      };
      this.onAddProduct(product);
    },
  }
}
</script>

<style scoped>
  form{
    display: flex;
    flex-direction: column;    
    background-color: rgb(219, 219, 219);
    border-radius: 10px;
    padding: 10px 30px 30px;
    width: 300px;

  }
  form p{
    color: white;
    font-size: 1.4em;
    font-weight: bold;
  }
  input{
    margin: 1%;
    line-height: 20px;
    padding: 10px;
    font-size: 1.1em;
    border: none;
  }

  input[type="submit"]{
    background-color: rgb(50, 170, 50);
    color: white;
    font-weight: bold;
    font-size: 1.2em;
  }
</style>