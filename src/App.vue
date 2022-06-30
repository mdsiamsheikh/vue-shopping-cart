<template>
  <div>
    <header>
    <button v-on:click="navigateTo('products')">View products</button>
    {{cart.length}} in cart 
    <button v-on:click="navigateTo('cart')">View Cart</button>
    </header>

    <div v-if="page === 'cart'">
      <cart-vew   v-on:removeItemFromCart="removeItemFromCart" :cart="cart"></cart-vew>
    </div>

   <div v-if="page === 'products'">
    <products-vew v-on:addItemToCart='addItemToCart'></products-vew>
   </div>
  </div>
</template>

<script>
  import ProductsVew from './components/ProductsVew.vue'
  import CartVew from './components/CartVew.vue'
export default {
     name: 'App',
     data: () => {
      return {
        page: 'products',
        cart: []       
      }
     },
     methods: {
      addItemToCart(product) {
        this.cart.push(product);
        console.log(this.cart);
      },
      removeItemFromCart(product) {
        this.cart.splice(this.cart.indexOf(product), 1);
      },
      navigateTo(page) {
        this.page = page;
      }
     },
    components: {
      ProductsVew,
      CartVew
    }
}
</script>

<style>
 body {
  margin: 0;
}
.products {
  display: grid;
  grid-template-columns: 1fr 1fr;
}
.products button {
  padding: 10px;
  background-color: black;
  color: white;
  outline: none;
  border: none;
  cursor: pointer;
}

 .img {
  height: 100%;
  width: 100%;
}
</style>

<style scored>

  header {
  height: 60px;
  box-shadow: 2px 2px 5px blue;
  background-color: rgba(177, 153, 66, 0.859);
  text-align: right;
  font-size: 30px;
  padding-top: 20px;
}

header button {
  padding: 10px;
  border: none;
  cursor: pointer;
  color: white;
  background-color: rgb(51, 129, 160);
}
</style>
         
           