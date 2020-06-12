<template>
  <div class='product' @click='$emit("select", product)'>
    <div class='name'>{{product.name}}</div>
    <div class='price'>${{product.price}}</div>
  </div>
</template>

<script>

export default {
  props: ['product']
}
</script>

<style>
  .product {
    border: 1px solid #eee;
    background: #fefefe;
    padding: 20px;
    margin: 10px 0;
  }
</style>