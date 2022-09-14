<template>
  <div>
    <div id="Header">
      {{props.outlet.address}}
    </div>
    <div id = "mainbody">
      <button @click="goLeft">Left</button>
      <div id="menuArea">
        <order-card v-for="Item of display.slice(startIndex,endIndex)"
                    :key="Item.id"
                    :name ="Item.name"
                    :desc = "Item.desc"
                    @increase="push(Item.name)"
                    @decrease="remove(Item.name)"></order-card>
      </div>
      <button @click="goRight">Right</button>
    </div>
  </div>
</template>

<script setup>
import {computed, defineProps, ref, toRefs,defineEmits} from "vue";
import OrderCard from "@/components/OrderCard";

const props = defineProps(
    {outlet:Object,
  menu:Object,
    orders:[]});

const startIndex = ref(0);
const endIndex = ref(4);
const {menu, orders} = toRefs(props);
function goRight(){
  startIndex.value+=4;
  endIndex.value +=4;
  console.log(startIndex, endIndex);
}
const emits = defineEmits('updateOrder');
function push(name) {
  orders.value.push(name);
  console.log(orders.value);
  emits('updateOrder');
}
function remove(name){
  if(orders.value.includes(name)) {
    const index = orders.value.indexOf(name);
    orders.value.splice(index,1);
  }
  console.log(orders.value);
  emits('updateOrder');
}
function goLeft(){
  startIndex.value-=4;
  endIndex.value-=4;
  console.log(startIndex, endIndex);
}
const display = computed(() => {
  var array = menu.value.offerings;
  if(array!== undefined){
    return array;
  }
  return [];
})
</script>

<style scoped>
*{
  background-color: #735D78;
  width: 100%;
  max-width: 100%;
}
#Header {
  background-color: #D1B3C4;
  height: 10vh;
  font-weight: bold;
  font-size: 8vh;
  font-family: Arial;

}
#mainbody{
  display: flex;
  flex-direction: row;
  justify-content: center;
  align-content: center;
}
#mainbody button{
  width: 5vw;
  height: 5vw;
  align-self: center;
  margin: 1vw;
  border-radius: 1vw;
  background-color: #F7D1CD;
  border: none;
  color: #524459;
  cursor: pointer;
}
#mainbody button:hover{
  background-color: #524459;
  color: #F7D1CD;
}
#menuArea{
  display: flex;
  width: 100%;
  max-width: 100%;
  max-height: 90vh;
  height: 90vh;
  flex-direction: row;
  flex-wrap: wrap;
  align-content: space-around;
  justify-content: center;
  overflow: clip;
}

</style>