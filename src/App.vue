<template>
  <div v-if="!sent" id = "Main">
    <sidebar :orders="orders" @sendOrder ="sendOrders"></sidebar>
    <Mainpane :outlet="outlet" :menu="menu" :orders="orders" @updateOrder="readOrders" ></Mainpane>
  </div>
  <OrderPlaced v-else @newOrder = "newOrder"></OrderPlaced>
</template>

<script setup>

import {computed, onMounted, ref} from "vue";
import axios from 'axios'
import sidebar from "@/components/Sidebar";
import Mainpane from"@/components/MainPane"
import OrderPlaced from "@/components/OrderPlaced"

const outlet = ref({});
const menu  = ref({});
const orders = ref([]);
const addr = computed(() =>{
  if(outlet.value === null) {
    return "";
  } else{
    return outlet.value.address;
  }
})
const sent = ref(false);
onMounted(() =>{axios.get("http://localhost:8080/outlet/Baker_St_123").then(
    response =>{(outlet.value = response.data);
      console.log(response.data)
    menu.value = response.data.menu;
    })});

function readOrders(){
  console.log(orders);
}

const order = ref({
    id: null,
    placedBy: null,
    items: orders.value,
    placedAt :undefined,
    'outletAddr': addr

})
function sendOrders() {
  console.log("Sending!")
  console.log(order)
  const result = axios.post("http://localhost:8080/order", order.value, {headers:{'Content-Type':'application/json; charset=utf-8'}}).then(res => {
    if(res.status === 200) {
      sent.value = true;
    }
  })
  console.log(result)
}
function newOrder() {
  sent.value = false;
}
</script>

<style>
*{
  margin: 0;
}
#Main{
  display: flex;
  flex-direction: row;;
  justify-content: space-between;
  height: 100%;
  width: 100%;
  margin: 0;
}
</style>
