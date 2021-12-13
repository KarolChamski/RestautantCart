<template>
  <div class="wrapper">
    <div class="cards">
      <the-menu class="card card-menu" @addToCart="addDish"></the-menu>
    </div>
  </div>
      <the-cart class="card card-cart" @click="showCart" :visible="visible" :cart="CartStatus"></the-cart>
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
      CartStatus: [],
      visible: false
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
    showCart(){
      this.visible = !this.visible
    }

  }
}
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

.wrapper {
  margin-right: auto; 
  margin-left:  auto;
  max-width: 1300px;
  padding-left:  0.5rem;
  padding-right: 0.5rem; 
}
.card-cart{
  position: fixed;
  bottom: 0px;
  width: 100%;
  box-shadow: 3px 3px 20px #0000001A;
  background-color: rgb(180, 151, 151);
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