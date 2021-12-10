<template>
  <h1>HELLO</h1>
</template>
<script>
export default {
  data() {
    return {
      dishes: [
        {
          title: "Jajka i bekon",
          price: "15zł",
          img: "plate__bacon-eggs.png"
        },
        {
          title: "Sałatka z kurczakiem",
          price: "25zł",
          img: "plate__chicken-salad.png" 
        },
        {
          title: "Paluszki rybne",
          price: "19zł",
          img: "plate__fish-sticks-fries.png"
        },
        {
          title: "Ravioli",
          price: "24zł",
          img: "plate__ravioli.png"
        },
        {
          title: "Łosoś z warzywami",
          price: "36zł",
          img: "plate__salmon-vegetables.png"
        },
        {
          title: "Spaghetti",
          price: "28zł",
          img: "plate__spaghetti-meal-sauce.png"
        },
        {
          title: "Włoskie przysmaki",
          price: "23zł",
          img: "plate.png"
        },
      ],
    };
  },
};
</script>
