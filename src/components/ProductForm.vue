<template>
  <div>
    <form @submit.prevent="onFormSubmit">
      <p>Cadastro de Produtos:</p>
      <input type="text" placeholder="Nome" v-model="name" required>
      <input type="number" placeholder="Preço" v-model="price" required>
      <input type="text" placeholder="Categoria" v-model="category" required>
      <input type="submit" value="Cadastrar">
    </form>
    <router-link to="/products">Visualizar lista de produtos cadastrados</router-link>
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
  },
  methods: {
    onFormSubmit(){
      const product = {
        name: this.name,
        price: this.price,
        category: this.category,
      };
      this.$store.dispatch('addProduct', product);
      this.name = '';
      this.price = '';
      this.category = '';
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
  a{
    text-decoration: none;
    display: flex;
    justify-content: center;
    margin-top: 15px;
    font-size: 1.2rem;
    color: chocolate;
  }
</style>