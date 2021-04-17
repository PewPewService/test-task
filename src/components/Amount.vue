<template>
    <div class="amount">
        <input type="button" id="minus" class="amounts disabled" :disabled="MinusDisable" ref="mD"  @click="onMinus()">
        <span id="amount" >{{count}}</span>
        <input type="button" class="amounts" id="plus" @click="onPlus()">
    </div>
</template>

<script>

export default{
    name:"Amount",
    props:{
        count:Number,
    },
    methods:{
        onMinus(){
            this.$emit('decreaseAmount');
            if (this.count == 2){
                this.MinusDisable=true;
                this.$refs.mD.className="amounts disabled";
            }
        },
        onPlus(){
            this.$emit('increaseAmount');
            this.MinusDisable=false;
            this.$refs.mD.className="amounts";
        }
    },
    created(){
        this.MinusDisable=true;
    }
}
</script>

<style scoped>
    .amounts{
        width:1.8rem;
        border-radius: 50%;
        border:0px;
        color:white;
        font-size: 1.4rem;
        text-align: center;
        margin-left: 1rem;
        line-height: height;
        cursor:pointer;
    }
    #minus{
        background-color: red;
        width:1.8rem;
        height:1.8rem;
        background-repeat: round;
        margin-right: 1rem;
        background-image: url("./../assets/minus.png");
    }
    #minus.disabled{
        background-color: gray;
    }
    #plus{
        background-color: rgb(156, 111, 75);
        width:1.8rem;
        height:1.8rem;
        background-repeat: round;
        background-image: url("./../assets/plus.png");
    }
    #amount{
        font-size: 1.4rem;
        align-self: right;
        color:black;
        vertical-align: super;
    }
    .amount{
        float: right;
    }
</style>
