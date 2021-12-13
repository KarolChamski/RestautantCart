<template>
  <div class="wrapper">
    <div class="cards">
      <the-menu class="card card-menu" @addToCart="addDish"></the-menu>
      <the-cart class="card card-cart" :cart="CartStatus"></the-cart>
    </div>
  </div>
</template>

<script>
import TheMenu from './components/TheMenu.vue';
import TheCart from './components/TheCart.vue';
export default{
  components: {
    TheMenu,
    TheCart
  },
  data(){
    return{
      CartStatus: []
    }
  },
  methods:{
    addDish(dish){
      if(this.CartStatus.some(item => item.title == dish.title)){
        dish.counter ++;
      }
      else{
        this.CartStatus.push(dish)
      }
    },

  }
}
</script>


<style>
* {
  box-sizing: border-box;
}

html {
  font-family: sans-serif;
}

body {
  margin: 0;
}

.wrapper {
  margin-right: auto; 
  margin-left:  auto;
  max-width: 1300px;
  padding-left:  0.5rem;
  padding-right: 0.5rem; 
}

.card-menu{
  position: relative;
}
.card-cart{
  position: absolute;
}


@media (min-width: 768px){
  .cards{
  display: flex;
  flex-direction: row;
}
.card-cart{
  position: relative;
}
}
</style>