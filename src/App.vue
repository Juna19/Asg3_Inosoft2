<template>
  <div>
    <h1>Jenis Produk yang ditawarkan</h1>
    <p> Silahkan klik tombol Button untuk pesen produk</p>
    <table class="Table">
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
        <product
          v-for="(product, index) in products"
          :key="index"
          :product="product"
          @add-to-cart="addToCart"
        ></product>
      </tbody>
    </table>
    <cart :cart="cart" @remove-from-cart="removeFromCart" @checkout="checkout"></cart>
  </div>
</template>

<script>
import Product from './Product.vue';
import Cart from './Cart.vue';

export default {
  components: {
    Product,
    Cart,
  },
  data() {
    return {
      products: [
        {
          name: 'Indomie',
          description: 'Seleraku',
          stock: 10,
          price: 20,
        },
        {
          name: 'Sate',
          description: 'Setiap Malam',
          stock: 5,
          price: 15,
        },
        {
          name: 'Bakso',
          description: 'Urat yang terbaik',
          stock: 20,
          price: 25,
        },
      ],
      cart: [],
    };
  },
  methods: {
    addToCart(product) {
      const cartItem = this.cart.find((item) => item.name === product.name);

      if (cartItem) {
        cartItem.quantity++;
      } else {
        this.cart.push({ ...product, quantity: 1 });
      }
    },
    removeFromCart(product) {
      const cartItemIndex = this.cart.findIndex((item) => item.name === product.name);

      if (cartItemIndex !== -1) {
        const cartItem = this.cart[cartItemIndex];
        if (cartItem.quantity > 1) {
          cartItem.quantity--;
        } else {
          this.cart.splice(cartItemIndex, 1);
        }
      }
    },
    checkout() {
      this.cart = [];
    },
  },
};
</script>

<style>
table{
  border: solid;
  table-layout: fixed;
  text-shadow: 10;
 
}
</style>
