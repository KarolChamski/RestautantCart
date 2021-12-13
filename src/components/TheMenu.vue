<template>
    <div class="the-menu">
      <div class="dish" v-for="dish in dishes" :key="dish.title">

        <div class="image">
          <img class="plate" :src="`/img/${dish.img}`" alt="" />
        </div>
        
        <div class="description">
          <h2>{{ dish.title }}</h2>
          <p>{{ dish.price }}zł</p>
          <button @click="addDish(dish)">Dodaj do koszyka</button>
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
          price: 39,
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
          title: "Tortellini",
          price: 26,
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
<style scoped>
.dish{
  display: flex;
}
.plate{
  width: 150px;
}

</style>
