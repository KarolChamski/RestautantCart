<template>
<div class="wrapper">
    
    <div class="the-cart">
        <div v-for="item in cart" :key="item.title">
            <p>{{item.title}}</p>
            <p>{{item.price * item.counter}}zł</p>
            <img :src="`/img/${item.img}`" alt="">
            <p>ilość: {{item.counter}}</p>
        </div>

        <div v-if="this.cart.length == 0" class="empty-cart">
        <p>Koszyk jest pusty</p>
        </div>

    </div>
</div>
</template>

<script>
export default{
    props:['cart'],
    computed:{
        totalPrice(item){
            return item.price * item.counter
        }
    },

}
</script>