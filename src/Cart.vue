<template>
    <div class="cart">
      <h2>Shopping Cart</h2>
      <table>
        <thead>
          <tr>
            <th>Name</th>
            <th>Description</th>
            <th>Stock</th>
            <th>Price</th>
            <th>Action</th>
          </tr>
        </thead>
        <tbody>
          <tr v-for="(item, index) in cart" :key="index">
            <td>{{ item.name }}</td>
            <td>{{ item.description }}</td>
            <td>{{ item.stock }}</td>
            <td>${{ item.price }}</td>
            <td>
              <button @click="removeFromCart(item)">Delete</button>
            </td>
          </tr>
        </tbody>
      </table>
      <button @click="checkout">Checkout</button>
    </div>
  </template>
  
  <script>
  export default {
    props: {
      cart: Array,
    },
    methods: {
      removeFromCart(product) {
        this.$emit('remove-from-cart', product);
      },
      checkout() {
        this.$emit('checkout');
      },
    },
  };
  </script>
  
  <style scoped>
  
  button{
    background-color: red;
  }

  </style>
  