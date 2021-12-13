<template>
<div class="wrapper">
    <div class="the-menu">
      <div class="dish" v-for="dish in dishes" :key="dish.title">

        <div class="image">
          <img class="plate" :src="`/img/${dish.img}`" alt="" />
        </div>
        
        <div class="description">
          <h2>{{ dish.title }}</h2>
          <p>{{ dish.description }}</p>
          <p class="dish-price">{{ dish.price }}zł</p>
          <button class="order-button" @click="addDish(dish)">Zamów</button>
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
          counter: 1
        },
        {
          title: "Sałatka z kurczakiem",
          price: 25,
          img: "plate__chicken-salad.png",
          description: "Sałata, kurczak, parmezan",
          counter: 1
        },
        {
          title: "Paluszki rybne",
          price: 19,
          img: "plate__fish-sticks-fries.png",
          description: "Paluszki ryble, frytki, sos",
          counter: 1
        },
        {
          title: "Ravioli",
          price: 24,
          img: "plate__ravioli.png",
          description: "Tradycyjne włoskie ravioli",
          counter: 1
        },
        {
          title: "Łosoś z warzywami",
          price: 39,
          img: "plate__salmon-vegetables.png",
          description: "Łosoś, warzywa",
          counter: 1
        },
        {
          title: "Spaghetti",
          price: 28,
          img: "plate__spaghetti-meat-sauce.png",
          description: "Spaghetti, sos pomidorowy",
          counter: 1
        },
        {
          title: "Tortellini",
          price: 26,
          img: "plate.png",
          description: "Tortellini nadziewane serem",
          counter: 1
        },
      ],
    };
  },
  methods: {
    addDish(item) {
      this.$emit('addToCart', item)
    },
  },
};
</script>
<style scoped>
h2{
  font-size: 24px;
  margin-bottom: 0;
}
.the-menu{
  padding-bottom: 65px;
}

p{
  font-size: 16px;
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
  margin-top: 0.5rem;
  border-radius: 10px;
}
.description{
  text-align: center;
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
  padding: 0.5rem 1rem;
  border: 0;
}

</style>
