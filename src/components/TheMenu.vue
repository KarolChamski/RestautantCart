<template>
<div class="wrapper">
    <div class="the-menu">
      <div class="dish" v-for="dish in dishes" :key="dish.title">

        <div class="image">
          <img class="plate" :src="`/img/${dish.img}`" alt="" />
        </div>
        
        <div class="description">
          <h2>{{ dish.title }}</h2>
          <p>{{ dish.price }}zł</p>
          <button @click="addDish(dish)">Zamów</button>
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
h2{
  font-size: 24px;
}
.the-menu{
  padding-bottom: 35px;
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
  height: 160px;
  background-color: rgb(255, 255, 255);
  box-shadow: 3px 3px 20px #0000001A;
  margin-top: 0.5rem;
  border-radius: 10px;
}
.description{
  text-align: center;
  width: 50%;
}
.description button{
  background-color: #FFB300;
  color: rgb(255, 255, 255);
  border: 0;
}

</style>
