<template>
  <div class="wrapper">
    <div class="the-menu">
      <dish-card v-for="dish in dishes" :key="dish.title">
        <template v-slot:image>
          <img :src="`/img/${dish.img}`" alt="" />
        </template>
        <template v-slot:description>
          <h2>{{ dish.title }}</h2>
          <p>{{ dish.price }}</p>
          <button @click="addDish(dish)">Dodaj do koszyka</button>
        </template>
      </dish-card>
    </div>
  </div>
</template>
<script>
import DishCard from "./DishCard.vue";
export default {
  components: {
    DishCard,
  },
  data() {
    return {
      dishes: [
        {
          title: "Jajka i bekon",
          price: 15,
          img: "plate__bacon-eggs.png",
          counter: 1
        },
        {
          title: "Sałatka z kurczakiem",
          price: 25,
          img: "plate__chicken-salad.png",
          counter: 1
        },
        {
          title: "Paluszki rybne",
          price: 19,
          img: "plate__fish-sticks-fries.png",
          counter: 1
        },
        {
          title: "Ravioli",
          price: 24,
          img: "plate__ravioli.png",
          counter: 1
        },
        {
          title: "Łosoś z warzywami",
          price: 36,
          img: "plate__salmon-vegetables.png",
          counter: 1
        },
        {
          title: "Spaghetti",
          price: 28,
          img: "plate__spaghetti-meat-sauce.png",
          counter: 1
        },
        {
          title: "Włoskie przysmaki",
          price: 23,
          img: "plate.png",
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
