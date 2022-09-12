<template>
  <div>
    <div id="Header">
      {{outlet.address}}
    </div>
    <div id = "mainbody">
      <button @click="goLeft">Left</button>
      <div id="menuArea">
        <order-card v-for="Item of menu.offerings" :key="Item.id" :name ="Item.name" :desc = "Item.desc"></order-card>
      </div>
      <button @click="goRight">Right</button>
    </div>
  </div>
</template>

<script setup>
import {defineProps, ref} from "vue";
import OrderCard from "@/components/OrderCard";
defineProps(
    {outlet:Object,
  menu:[]});
const startIndex = ref(0);
const endIndex = ref(4);
function goRight(){
  startIndex.value+=4;
  endIndex.value +=4;
  console.log(startIndex, endIndex);
}
function goLeft(){
  startIndex.value-=4;
  endIndex.value-=4;
  console.log(startIndex, endIndex);
}
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
  flex-direction: row;
  flex-wrap: wrap;
  align-content: space-between;
  justify-content: center;
  overflow: clip;
}

</style>