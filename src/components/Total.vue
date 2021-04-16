<template>
    <div>
        <button class="total">
            <img class="cart">
            Добавить {{count}} в корзину
            <span class="sum">{{count*(bp+mp+sp+cp)}}</span>
        </button>
    </div>
</template>

<script>
    export default{
        name:"Total",
        props:{
            count:Number,
            bp: Number,
            mp: Number,
            sp: Number,
            cp: Number
        }
    }
</script>

<style scoped>
.total{
    margin-top:2rem;
    margin-bottom:1rem;
    height:2rem;
    color:white;
    background-color: black;
    margin-left: 1rem;
    margin-right: 1rem;
    width:-webkit-fill-available;
}
.sum{
    float:right;
    color:white;
}
.cart{
    content:url("./../assets/cart.png");
    height: 1rem;
    float:left;
    width: auto;
}
</style>