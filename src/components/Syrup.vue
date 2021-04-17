<template>
    <div>
        <div class="name">
            {{syrupsDesc.name}}<span class="required" v-if="syrupsDesc.required">(REQUIRED)</span>
            <span class="radios" @click="Clear()">reset</span>
        </div>
        <div class="additional" v-if="syrupsDesc.additional">{{syrupsDesc.additional}}</div>
        <p class="choices" v-for="syrup in syrups" :key="syrup.id" @click="SelectSyrup(syrup.id,syrup.price)">
            {{syrup.name}}
            <span :id="syrup.id" v-if="syrup.price>0">
                 ({{currency}} {{syrup.price}})
            </span>
            <input type="radio" name="syrup" :value="syrup.id" ref="radio">
            <span class="checkmark"></span>
        </p>
    </div>
</template>

<script>
export default({
    name:"Syrup",
    props:{
        syrupsDesc: Object,
        syrups: Array,
        currency: String,
    },
    methods:{
        Clear(){
            this.$refs.radio.forEach(element => {
                element.checked=false;
            });
            this.$emit("selectSyrup", 0);
        },
        SelectSyrup(id, price){
            this.$refs.radio[id-1].checked=true;
            this.$emit("selectSyrup", price);
        }
    }
})
</script>

<style scoped>
.radios{
    font-size: 1rem;
    line-height: height;
    cursor: pointer;
}
</style>
