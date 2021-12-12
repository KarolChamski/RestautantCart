<template>
<div class="wrapper">
    
    <div class="the-cart">
        <div v-for="item in cart" :key="item.title">

            <div class="cart-item" v-if="item.counter != 0">

            <p>{{item.title}}</p>
            <p>{{item.price * item.counter}}zł</p>
            <img :src="`/img/${item.img}`" alt="">
            <div class="counter-box">
            <button @click="reduceCounter(item)"><img src="../assets/chevron.svg" alt=""></button>
            <p>ilość: {{item.counter}}</p>
            <button @click="addCounter(item)"><img  src="../assets/chevron-right.svg" alt=""></button>
            </div>

            </div>



        </div>
        <h3>Łączna kwota: {{totalPrice}} zł</h3>
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

</style>