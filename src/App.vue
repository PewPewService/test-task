<template>
  <div id="app">
    <link rel="preconnect" href="https://fonts.gstatic.com">
    <link href="https://fonts.googleapis.com/css2?family=Noto+Sans&display=swap" rel="stylesheet">
    <img src="./assets/raph.jpg">
    <div>
           <p class="coffeeName"> {{coffeeName}} </p>
           <p class="desc"> {{description}} </p>
        </div>
        <div class="price"> {{currency}} {{basePrice}} </div>
        <Amount :count="count" @decreaseAmount="decrease" @increaseAmount="increase" />
        <Milk :milks="milks" :milksDesc="milksDesc" :currency="currency" @selectMilk="selectMilk" />
        <Syrup :syrups="syrups" :syrupsDesc="syrupsDesc" :currency="currency" @selectSyrup="selectSyrup" />
        <Chocolate :chocs="chocs" :chocsDesc="chocsDesc" :currency="currency" @selectChocolate="selectChocolate" />
        <Total :count="count" :bp="basePrice" :mp="milksprice" :sp="syrupsprice" :cp="chocsprice" :currency="currency" />
        
  </div>
</template>

<script>
  import Amount from './components/Amount.vue'
  import Milk from './components/Milk.vue'
  import Syrup from './components/Syrup.vue'
  import Chocolate from './components/Chocolate.vue'
  import Total from './components/Total.vue'

  export default {
    name: 'App',
    components: {
      Amount,
      Milk,
      Syrup,
      Chocolate,
      Total
    },
    data(){
      return {
        imgsrc:String,
        coffeeName:String,
        description:String,
        basePrice:Number,
        currency:String,
        count: Number,
        totalPrice: Number,
        milksDesc:String,
        milks:[],
        milksprice: Number,
        syrupsDesc:String,
        syrups:[],
        syrupsprice: Number,
        chocsDesc:String,
        chocs:[],
        chocsprice: Number,
      }
    },
    methods:{
      increase(){
        this.count+=1;
      },
      decrease(){
        this.count-=1;
      },
      selectMilk(mp){
        this.milksprice=mp;
      },
      selectSyrup(sp){
        this.syrupsprice=sp; 
      },
      selectChocolate(cp){
        this.chocsprice=cp;
      }
    },
    created(){
      this.coffeeName="Раф";
      this.description="Описание";
      this.basePrice=60;
      this.currency="₽";
      this.count=1;
      this.milksDesc="Молоко";
      this.milks=[
        {
          id:1,
          name:"молоко1",
          price:0,
        },
        {
          id:2,
          name:"Молоко2",
          price:20,
        }
      ];
      this.milksprice=0;
      this.syrupsDesc="Сиропы",
      this.syrups=[
        {
          id:1,
          name:"Сироп1",
          price:33,
        },
        {
          id:2,
          name:"Сироп2",
          price:29,
        }
      ],
      this.syrupsprice=0;
      this.chocsDesc="Шоколад",
      this.chocs=[
        {
          id:1,
          name:"Шоколад1",
          price:69
        },
        {
          id:2,
          name:"Шоколад 2",
          price:59
        },
        {
          id:3,
          name:"шоколад3",
          price:74
        }
      ],
      this.chocsprice=0;
    }
  }
</script>

<style>
    @media(min-width:800px){
        #app{
            margin-left: 35%;
            margin-right: 35%;
            background-color: white;
        }
        body{
          background-color: lightsteelblue;
          font-family: 'Noto Sans', sans-serif;
        }
    }
    body{
      margin:0px
    }
    img{
        width:100%;
        height:auto;
    }
    .coffeeName{
      text-align: center;
      font-size:1.5rem;
    }
    .desc{
      text-align: center;
      font-size:0.9rem;
      color:gray;
    }
    .price{
      font-size: 1.4rem;
        text-align: left;
        display: inline-block;
        padding-left: 1rem;
    }
    .amount{
      float:right;
      padding-right: 1rem;
      display: inline;
    }
</style>
