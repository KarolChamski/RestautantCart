<template>
<h1>YOUR RESTAURANT CART<i class="fas fa-pepper-hot"></i></h1>
  <div class="app-mobile">
    <div class="wrapper">
      <div class="cards">
        <the-menu class="card card-menu" @addToCart="addDish"></the-menu>
      </div>
    </div>
    <div class="cart-bar" @click="showCart">
      Koszyk ({{ CartStatus.length }})
    </div>
    <the-cart
      :mobile="true"
      @close="showCart"
      :class="{ 'card-cart-show': cartVisible }"
      class="card card-cart"
      :visible="cartVisible"
      :cart="CartStatus"
    ></the-cart>
  </div>

  <div class="app-desktop">
    <div class="wrapper">
      <div class="cards">
        <the-menu class="card card-menu" @addToCart="addDish"></the-menu>      
        <the-cart
          :mobile="false"
          @close="showCart"
          class="card card-cart"
          :visible="true"
          :cart="CartStatus"
        ></the-cart>
      </div>
    </div>
  </div>
</template>

<script>
import TheMenu from "./components/TheMenu.vue";
import TheCart from "./components/TheCart.vue";
export default {
  components: {
    TheMenu,
    TheCart,
  },
  data() {
    return {
      CartStatus: [],
      cartVisible: false,
    };
  },
  methods: {
    addDish(dish) {
      if (this.CartStatus.some((item) => item.title == dish.title)) {
        dish.counter++;
      } else {
        this.CartStatus.push(dish);
      }
    },
    showCart() {
      this.cartVisible = !this.cartVisible;
    },
  },
};
</script>

<style>
* {
  box-sizing: border-box;
  overflow-x: hidden;
}

html {
  font-family: sans-serif;
}

body {
  margin: 0;
}
h1{
  width: 100%;
  text-align: center;
  font-family: 'poppins', sans-serif;
  color: #000000;
}
h1 i{
  color: #FFB300;
}
h2{
  text-align: left;
  margin-left: 0.5rem;
  font-size: 36px;
}
button{
  cursor: pointer;
}

.wrapper {
  margin-right: auto;
  margin-left: auto;
  max-width: 1300px;
  padding-left: 0.5rem;
  padding-right: 0.5rem;
}
.app-desktop {
  display: none;
}
.card-cart {
  bottom: 0;
  width: 100%;
  background-color: #fff;
}
.card-cart-show {
  position: fixed;
  top: 0;
}

.cart-bar {
  position: fixed;
  bottom: 0;
  padding: 1rem 0;
  width: 100%;
  box-shadow: 3px 3px 20px #0000001a;
  background-color: rgb(255, 255, 255);
  font-size: 30px;
  text-align: center;
}

@media (min-width: 768px) {
  .app-mobile {
    display: none;
  }
  .app-desktop {
    display: block;
  }
  .cards {
    display: flex;
    justify-content: center;
    flex-direction: row;
  }
  .card-cart {
    position: relative;
    top: 0;
    width: 100%;
    background-color: rgb(255, 255, 255);
  }
  .card-menu {
    width: 100%;
  }
}
</style>
