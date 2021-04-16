<template>
    <div>
        <div class="name">{{milksDesc}}</div>
        <p class="choices" v-for="milk in milks" :key="milk.id" @click="SelectMilk(milk.id, milk.price)">
            {{milk.name}}
            <span :id="milk.id" v-if="milk.price>0">
                 ({{currency}} {{milk.price}})
            </span>
            <input type="radio" name="milk" ref="radios" :value="milk.id">
            <span class="checkmark"></span>
        </p>
    </div>
</template>

<script>
export default{
    name:"Milk",
    props:{
        milks: Array,
        milksDesc: String,
        currency: String,
    },
    methods:{
        SelectMilk(id,price){
            this.$refs.radios[id-1].checked=true;
            this.$emit("selectMilk",price);
        }
    },
    mounted(){
        this.$refs.radios[0].checked=true;
    }
}
</script>

<style>
    .name{
        margin-top:1rem;
        padding: 1rem;
        font-size: 1.5rem;
        text-align: left;
        height: 2rem;
        background-color: lightgray;

    }

    .choices {
        border-bottom: lightgray solid 1px;
        padding-left: 1rem;
        padding-right: 1rem;
        padding-bottom: 1rem;
        display: block;
        position: relative;
        cursor: pointer;
        -webkit-user-select: none;
        -moz-user-select: none;
        -ms-user-select: none;
        user-select: none;
    }

    .choices input {
    position: absolute;
    opacity: 0;
    cursor: pointer;
    height: 0;
    width: 0;
    }

    .checkmark {
        float:right;
        margin-right: 1rem;
        height: 1rem;
        width: 1rem;
        background-color: white;
        border-radius: 50%;
        border: solid 3px gray;
    }

    .choices:hover input ~ .checkmark {
    background-color: gainsboro;
    }

    .choices input:checked ~ .checkmark {
    background-color: white;
    }

    .checkmark:after {
    content: "";
    position: absolute;
    display: none;
    }

    .choices input:checked ~ .checkmark:after {
    display: block;
    }

    .choices .checkmark:after {
    right:2.45rem;
    top: 0.45em;
    height: 0.5rem;
    width: 0.5rem;
    float:right;
    border-radius: 50%;
    background: gray;
    }

    .choices:last-of-type{
        border-bottom: 0px;
        padding-bottom: 0rem;
    }

    .radios{
        float:right;
        margin-right: 1rem;
        color:black;
    }

    body{
        margin:0px;
    }

    span{
        color:gray;
    }
</style>
