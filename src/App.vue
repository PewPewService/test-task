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
      this.coffeeName="Flat White";
      this.description="Freshly-ground beans and steamed milk";
      this.basePrice=125;
      this.currency="$";
      this.count=1;
      this.milksDesc="MILK OPTION";
      this.milks=[
        {
          id:1,
          name:"Full Milk",
          price:0,
        },
        {
          id:2,
          name:"Skim Milk",
          price:0,
        },
        {
          id:3,
          name:"Soy Milk",
          price:20,
        }
      ];
      this.milksprice=0;
      this.syrupsDesc="SYRUP OPTION",
      this.syrups=[
        {
          id:1,
          name:"Nutty",
          price:10,
        },
        {
          id:2,
          name:"Cherry",
          price:10,
        },
        {
          id:3,
          name:"Chocolade",
          price:10,
        }
      ],
      this.syrupsprice=0;
      this.chocsDesc="CHOCOLADE",
      this.chocs=[
        {
          id:1,
          name:"Toblerone",
          price:70
        },
        {
          id:2,
          name:"Patchi",
          price:60
        },
        {
          id:3,
          name:"Spartak",
          price:40
        }
      ],
      this.chocsprice=0;
    }
  }
</script>

<style>
    @media(min-width:500px){
      body{
        background-color: lightsteelblue;
      }
      #app{
        background-color: white;
      }
    }
    @media(min-width:500px) and (max-width:700px){
        #app{
            margin-left: 15%;
            margin-right: 15%;
        }
    }
    @media(min-width:701px) and (max-width:1000px){
        #app{
            margin-left: 22%;
            margin-right: 22%;
        }
    }
    @media(min-width:1001px){
        #app{
            margin-left: 32%;
            margin-right: 32%;
        }
    }
    body{
      margin:0px;
      font-family: 'Noto Sans', sans-serif;
    }
    img{
        width:100%;
        height:auto;
    }
    .coffeeName{
      text-align: center;
      font-size:1.5rem;
      margin-bottom: 0px;
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
