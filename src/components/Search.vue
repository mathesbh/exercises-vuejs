<template>
  <div>
    <input type="text" placeholder="Buscar" v-model="search" v-on:keyup="handleSearch">
  </div>
</template>

<script>
export default {
  name: "Search",
  components: {

  },
  props: {
    onSearch: Function,
  },
  data(){
    return {
      search: '',
    }
  },
  methods: {
    handleSearch(){
      this.onSearch(this.search);
    }
  }
}
</script>

<style scoped>
  input{
    padding: 10px;
    margin-bottom: 2%;
  }
</style>