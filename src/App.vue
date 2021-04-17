<template>
  <div id="app">
    <div class="back"></div>
    <link rel="preconnect" href="https://fonts.gstatic.com">
    <link href="https://fonts.googleapis.com/css2?family=Noto+Sans&display=swap" rel="stylesheet">
    <img src="./assets/raph.jpg">
    <div>
           <p class="coffeeName"> {{coffeeName}} </p>
           <p class="desc"> {{description}} </p>
        </div>
        <div>
          <div class="price"> {{currency}} {{basePrice}} </div>
          <Amount :count="count" @decreaseAmount="decrease" @increaseAmount="increase" />
        </div>
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
        milksDesc:[],
        milks:[],
        milksprice: Number,
        syrupsDesc:[],
        syrups:[],
        syrupsprice: Number,
        chocsDesc:[],
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
      this.milksDesc={
        name:"MILK OPTION",
        required:true,
        additional:"Please select 1 item"
      };
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
      this.syrupsDesc={
        name:"SYRUP OPTION",
        required:false,
        additional:""
      },
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
      this.chocsDesc={
        name:"CHOCOLADE",
        required:false,
        additional:""
      };
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
      font-weight: bold;
    }
    .desc{
      text-align: center;
      font-size:0.9rem;
      color:gray;
      padding-bottom: 1rem;
      border-bottom: 1px lightgray solid;
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
    .back{
      background-color: rgb(253, 255, 255);
      border-radius: 50%;
      position: absolute;
      width: 1.5rem;
      height: 1.5rem;
      margin:1rem;
      background-image: url("./assets/arrow.png");
      background-repeat: round;
      border: 0.5rem solid rgb(253, 255, 255);
    }
    .back:hover{
      background-color: rgb(200, 230, 250);
      border: 0.5rem solid rgb(200, 230, 250);
    }
</style>
