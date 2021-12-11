<template>
  <div class="wrapper">
    <div class="cards">
      <the-menu @addToCart="addDish"></the-menu>
      <the-cart :cart="CartStatus"></the-cart>
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

.cards{
  display: flex;
  flex-direction: row;
}
</style>