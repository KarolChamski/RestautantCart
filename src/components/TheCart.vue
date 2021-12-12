<template>
<div class="wrapper">
    
    <div class="the-cart">
        <div v-for="item in cart" :key="item.title">
            <p>{{item.title}}</p>
            <p>{{item.price * item.counter}}zł</p>
            <img :src="`/img/${item.img}`" alt="">
            <p>ilość: {{item.counter}}</p>
        </div>
        <h3>Łączna kwota: {{totalPrice}}</h3>

        <div v-if="this.cart.length == 0" class="empty-cart">
        <p>Koszyk jest pusty</p>
        </div>

    </div>
</div>
</template>

<script>
export default{
    data(){
        return{
            totalPrice: 0
        }
    },
    props:['cart'],
    methods:{
        sumPrice(){
            const priceArr = this.cart.map(item => item.price * item.counter);
            const totalPrice = priceArr.reduce((acc,cur)=> acc + cur ,0);
           this.totalPrice = totalPrice
        }
    },
    
    updated(){
        this.sumPrice()
    }

}
</script>