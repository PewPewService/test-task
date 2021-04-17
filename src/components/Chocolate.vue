<template>
    <div>
        <div class="name">
            {{chocsDesc}}
        </div>
        <p class="container" v-for="choc in chocs" :key="choc.id" @click="SelectChocolate(choc.id)">
            {{choc.name}}
            <span :id="choc.id" v-if="choc.price>0">
                 ({{currency}} {{choc.price}})
            </span>
            <input type="checkbox" name="check" :value="choc.price" ref="checks">
            <span class="mark"></span>
        </p>
    </div>
</template>

<script>
export default({
    name:"Chocolate",
    props:{
        chocsDesc: String,
        chocs: Array,
        currency: String,
    },
    methods:{
        SelectChocolate(id){
            let price=0;
            this.$refs.checks[id-1].checked= this.$refs.checks[id-1].checked ? false : true;
            this.$refs.checks.forEach(element => {
                if (element.checked) price+=Number(element.value);
            });
            this.$emit("selectChocolate",price);
        }
    }
})
</script>

<style scoped>
.container {
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

.container:last-of-type{
  border-bottom: 0px;
}

.container input {
  position: absolute;
  opacity: 0;
  cursor: pointer;
  height: 0;
  width: 0;
}

.mark {
  float:right;
  margin-right: 1rem;
  height: 1rem;
  width: 1rem;
  background-color: white;
  border: solid 3px gray;
}

.container:hover input ~ .mark {
  background-color: #ccc;
}

.container input:checked ~ .mark {
  background-color: white;
}

.mark:after {
  content: "";
  position: absolute;
  display: none;
}

.container input:checked ~ .mark:after {
  display: block;
}

.container .mark:after {
  right:2.43rem;
    top: 0.43em;
    height: 0.5rem;
    width: 0.5rem;
    float:right;
    background-color: gray;
}
</style>
