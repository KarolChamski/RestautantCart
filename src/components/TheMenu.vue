<template>
<div class="wrapper">
    <div class="the-menu">
      <h2>Menu</h2>
      <div class="dish" v-for="dish in dishes" :key="dish.title">

        <div class="image">
          <img class="plate" :src="`/img/${dish.img}`" alt="" />
        </div>
        
        <div class="description">
          <h3>{{ dish.title }}</h3>
          <p>{{ dish.description }}</p>
          <p class="dish-price">{{ dish.price }}zł</p>
          <button v-if="!dish.inCart" class="order-button" @click="addDish(dish)">Zamów</button>
          <button v-if="dish.inCart"  class="order-button">W koszyku</button>

        </div>
        
      </div>
    </div>
</div>
</template>
<script>

export default {

  data() {
    return {
      dishes: [
        {
          title: "Jajka i bekon",
          price: 15,
          img: "plate__bacon-eggs.png",
          description: "Jajko sadzone, boczek, tost",
          counter: 1,
          inCart: false
        },
        {
          title: "Sałatka z kurczakiem",
          price: 25,
          img: "plate__chicken-salad.png",
          description: "Sałata, kurczak, parmezan",
          counter: 1,
          inCart: false
        },
        {
          title: "Paluszki rybne",
          price: 19,
          img: "plate__fish-sticks-fries.png",
          description: "Paluszki ryble, frytki, sos",
          counter: 1,
          inCart: false
        },
        {
          title: "Ravioli",
          price: 24,
          img: "plate__ravioli.png",
          description: "Tradycyjne włoskie ravioli",
          counter: 1,
          inCart: false
        },
        {
          title: "Łosoś z warzywami",
          price: 39,
          img: "plate__salmon-vegetables.png",
          description: "Łosoś, warzywa",
          counter: 1,
          inCart: false
        },
        {
          title: "Spaghetti",
          price: 28,
          img: "plate__spaghetti-meat-sauce.png",
          description: "Spaghetti, sos pomidorowy",
          counter: 1,
          inCart: false
        },
        {
          title: "Tortellini",
          price: 26,
          img: "plate.png",
          description: "Tortellini nadziewane serem",
          counter: 1,
          inCart: false
        },
      ],
    };
  },
  methods: {
    addDish(item) {
      this.$emit('addToCart', item);
      item.inCart = !item.inCart
    },
  },
};
</script>
<style scoped>
h3{
  font-size: 24px;
  margin-bottom: 0;
}
.the-menu{
  padding-bottom: 80px;
box-shadow: 3px 3px 20px #0000001A;
}

.plate{
  width: 135px;
}
.dish{
  display: flex;
  align-items: center;
  height: 220px;
  background-color: rgb(255, 255, 255);
  box-shadow: 3px 3px 20px #0000001A;
  margin-top: 2rem;
  border-radius: 10px;
}
.description{
margin-left: 1rem;
  width: 50%;
}
.description p{
  margin: 0.5rem;
}
.dish-price{
  font-weight: 600;
}

.description button{
  background-color: #FFB300;
  color: rgb(255, 255, 255);
  padding: 0.5rem 1.8rem;
  border: 0;
}

</style>
