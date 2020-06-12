<template>
  <div id="app">
    <div>Count: {{count}}</div>
    <button @click.prevent='increment'>Increment</button>

    <h1>Products</h1>

    <div v-if='!loading' class='products'>
      <Product 
        v-for='product in products' 
        :key='product.name' 
        :product='product'
        @select='handleProductClick' />
    </div>
    <div v-else>
      Loading products...
    </div>

    <h1>New Product</h1>

    <form @submit.prevent='handleNewProductSubmit'>
      <div class="field">
        <label>Name</label>
        <input type="text" name="name" v-model='newProduct.name' />
      </div>
      <div class="field">
        <label>Price</label>
        <input type="text" name="price" v-model.number='newProduct.price' />
      </div>
      <div class="actions">
        <input type='submit' />
      </div>
    </form>
  </div>
</template>

<script>
import Product from './components/Product.vue'

export default {
  name: 'App',
  components: {
    Product
  },
  data() {
    return {
      count: 0,
      showDetails: false,
      loading: true,
      products: [],
      newProduct: {
        name: '',
        price: 0.00,
      },
    };
  },
  created() {
    this.products = [
      { name: "Macbook Pro", price: 2399 },
      { name: "Macbook Air", price: 999 },
    ];
    this.loading = false;
  },
  methods: {
    increment() {
      this.count++;
    },
    toggleDetails() {
      this.showDetails = !this.showDetails
    },
    handleNewProductSubmit() {
      this.products.push(this.newProduct);
      this.newProduct = { name: '', price: 0.00 };
    },
    handleProductClick(product) {
      alert(`${product.name} clicked!`);
    }
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
