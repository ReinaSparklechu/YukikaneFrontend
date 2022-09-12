<template>
    <div id = "Main">
    <sidebar></sidebar>
    <Mainpane :outlet="outlet" :menu="menu"></Mainpane>
  </div>
</template>

<script setup>

import {onMounted, ref} from "vue";
import axios from 'axios'
import sidebar from "@/components/Sidebar";
import Mainpane from"@/components/MainPane"

const outlet = ref({});
const menu  = ref({});
onMounted(() =>{axios.get("http://localhost:8080/outlet/Baker_St_123").then(
    response =>{(outlet.value = response.data);
      console.log(response.data)
    menu.value = response.data.menu;
    })});
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
