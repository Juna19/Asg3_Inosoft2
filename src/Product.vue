<template>
  <tr>
    <td>{{ product.name }}</td>
    <td>{{ product.description }}</td>
    <td>{{ product.stock }}</td>
    <td>${{ product.price }}</td>
    <td>
      <button @click="addToCart">Button</button>
    </td>
  </tr>
</template>

<script>
export default {
  props: {
    product: Object,
  },
  methods: {
    addToCart() {
      this.$emit('add-to-cart', this.product);
    },
  },
};
</script>

<style>
button{
  background-color: blue;
}
</style>
