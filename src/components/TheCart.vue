<template>
<div class="wrapper">
    
    <div class="the-cart" v-if="visible">
        <div class="close-div">
        <h2>Koszyk</h2>
        <button class="close" v-if="mobile" @click="$emit('close')"><img src="../assets/close.svg" alt="krzyżyk, znak wyjścia"></button>
        </div>

        <p v-if="this.cart.length == 0" class="empty-cart">Koszyk jest pusty</p>

        <div v-for="item in cart" :key="item.title">

            <div class="cart-item" v-if="item.counter != 0">

           <div class="item-image">
            <img class="plate" :src="`/img/${item.img}`" alt="">
               </div>         

               <div class="item-description">
            <p class="item-title">{{item.title}}</p>
            <p class="item-price">{{item.price}}zł</p>
            <div class="counter-box">
            <button class="arrow" @click="reduceCounter(item)"><img class="arrow-img" src="../assets/arrow-left.svg" alt=""></button>
            <p class="counter">{{item.counter}}</p>
            <button class="arrow" @click="addCounter(item)"><img class="arrow-img" src="../assets/arrow-right.svg" alt=""></button>
            <p class="item-total-price">{{item.price * item.counter}}zł</p>


            </div>
               </div>


            

        </div>
        
        </div>
        <h3 v-if="cart.length > 0">Łączna kwota: {{totalPrice}} zł</h3>

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
            if(item.counter == 0){
                item.inCart = false
            }
        }
    },
    
    updated(){
        this.sumPrice()
    }

}
</script>
<style>
.the-cart{
    box-shadow: 3px 3px 20px #0000001A;
}
.counter-box{
    display: flex;
    margin-top: 1rem;
}
.counter{
    padding: 0 1rem;
    font-weight: 600;
}
h2{
    margin-bottom: 30px;
    text-align: center;
}
.plate{
    width: 125px;
}
.close-div{
    display: flex;
    justify-content: space-between;
}
.close{
    width: 25px;
    height: 25px;
    margin: 0.2rem;
    padding: 0;
    background: none;
    border: none;
}

.arrow{
padding: 0;
margin: 0;
border: none;
background-color: #FFB300;
border-radius: 5px;
height: 25px;
width: 20px;
}

.counter{
    margin: 0;
    top: 0;
}
.cart-item{
    display: flex;
    margin-bottom: 2rem;
    background-color: #fff;
}
.item-description{
    display: flex;
    flex-direction: column;
}
.item-title{
    margin-bottom: 0;
}
.item-price{
    margin: 0;
}
.item-total-price{
    font-size: 18px;
    font-weight: 600;
    margin: 0 1rem;
}


</style>