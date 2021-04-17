<template>
    <div>
        <button class="total">
            <img class="cart">
            ADD {{count}} TO CART
            <span class="sum">{{currency}}{{count*(bp+mp+sp+cp)}}</span>
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
            cp: Number,
            currency: String
        }
    }
</script>

<style scoped>
.total{
    margin-top:2rem;
    margin-bottom:1rem;
    height:2.5rem;
    font-size: 1rem;
    color:white;
    background-color: rgb(55, 40, 33);
    margin-left: 2rem;
    margin-right: 2rem;
    width:-webkit-fill-available;
    border:0px;
    border-radius: 0.1rem;
    cursor: pointer;
    padding-right: 1rem;
    padding-left:1rem;
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