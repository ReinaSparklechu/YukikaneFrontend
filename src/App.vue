<template>
    <div id = "Main">
    <sidebar :orders="orders" @sendOrder ="sendOrders"></sidebar>
    <Mainpane :outlet="outlet" :menu="menu" :orders="orders" @updateOrder="readOrders" ></Mainpane>
  </div>
</template>

<script setup>

import {onMounted, ref} from "vue";
import axios from 'axios'
import sidebar from "@/components/Sidebar";
import Mainpane from"@/components/MainPane"

const outlet = ref({});
const menu  = ref({});
const orders = ref([]);
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
    items: orders,
    placedAt :undefined,
    outlet: outlet

})
function sendOrders() {
  console.log("Sending!")
  var obj = {};
  obj['id'] = 1;
  console.log(order)
  const result = axios( {
    method: 'post',
    url: 'http://localhost:8080/order',
    data: {

    },
    params: {
        order: {
          id: null,
          placedBy: null,
          items: order.value.items,
          placedAt: Date.now(),
          outlet: null
        }
    },
  })
  console.log(result)
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
