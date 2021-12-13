<template>
<div class="wrapper">
    
    <div class="the-cart" v-if="visible">
        <div class="close-div">
        <h2>Koszyk</h2>
        <button v-if="mobile" @click="$emit('close')"><img src="../assets/chevron.svg" alt="krzyżyk, znak wyjścia"></button>
        </div>


        

        <p v-if="this.cart.length == 0" class="empty-cart">Koszyk jest pusty</p>

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
    props:['cart', 'visible', 'mobile'],
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
    margin-bottom: 30px;
    font-size: 28px;
}
.plate{
    width: 145px;
}
.close-div{
    display: flex;
    justify-content: space-between;
}


</style>