<template>
<div class="wrapper">
    
    <div class="the-cart">
        <h2>Koszyk</h2>
        <p v-if="this.cart.length == 0" class="empty-cart">Koszyk jest pusty</p>

        <div class="cart-visible" v-if="visible">

        <div v-for="item in cart" :key="item.title">

            <div class="cart-item" v-if="item.counter != 0">

            <p>{{item.title}}</p>
            <p>{{item.price * item.counter}}zł</p>
            <img class="plate" :src="`/img/${item.img}`" alt="">
            <div class="counter-box">
            <button @click="reduceCounter(item)"><img src="../assets/chevron.svg" alt=""></button>
            <p>ilość: {{item.counter}}</p>
            <button @click="addCounter(item)"><img  src="../assets/chevron-right.svg" alt=""></button>
            </div>

            </div>

        </div>
        <h3 v-if="cart.length > 0">Łączna kwota: {{totalPrice}} zł</h3>
        
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
    props:['cart', 'visible'],
    methods:{
        sumPrice(){
            const priceArr = this.cart.map(item => item.price * item.counter);
            const totalPrice = priceArr.reduce((acc,cur)=> acc + cur ,0);
           this.totalPrice = totalPrice
        },
        addCounter(item){
            item.counter = item.counter +1
        },
        reduceCounter(item){
            item.counter = item.counter -1;
            
        }
    },
    
    updated(){
        this.sumPrice()
    }

}
</script>
<style>

.counter-box{
    display: flex;
}
h2{
    padding-top: 1rem;
    margin-bottom: 100px;
    font-size: 28px;
}
.plate{
    width: 145px;
}


</style>