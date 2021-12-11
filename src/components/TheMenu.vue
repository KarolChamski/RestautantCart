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
          price: "15zł",
          img: "plate__bacon-eggs.png",
        },
        {
          title: "Sałatka z kurczakiem",
          price: "25zł",
          img: "plate__chicken-salad.png",
        },
        {
          title: "Paluszki rybne",
          price: "19zł",
          img: "plate__fish-sticks-fries.png",
        },
        {
          title: "Ravioli",
          price: "24zł",
          img: "plate__ravioli.png",
        },
        {
          title: "Łosoś z warzywami",
          price: "36zł",
          img: "plate__salmon-vegetables.png",
        },
        {
          title: "Spaghetti",
          price: "28zł",
          img: "plate__spaghetti-meat-sauce.png",
        },
        {
          title: "Włoskie przysmaki",
          price: "23zł",
          img: "plate.png",
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
