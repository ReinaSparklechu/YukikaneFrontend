<template>
<div class="card">
  <div class="name">{{name}}</div>
  <div class="image"><img src="@/assets/coffee.png" alt="" srcset=""></div>
  <div class="desc">{{desc}}</div>
  <div id="footer">
    <button @click="amount>0? amount--:'' ">-</button>
    <p class="amt">{{amount}}</p>
    <button @click="amount++">+</button>
  </div>
</div>
</template>

<script setup>
import {defineProps, ref} from "vue";

defineProps({
  name:String,
  desc:String
})
const amount = ref(0);
</script>

<style scoped>
.card{
  width: 20vw;
  height: 35vh;
  background-color: #D1B3C4 ;
  margin: 10px;
  border: 4px solid #B392AC;
  border-radius: 5%;
  padding: 2%;
  display: flex;
  flex-direction: column;
}
.name {
  padding: 4px;
  height: 10%;
  background-color: #F7D1CD;
  text-align: left;
  text-justify: auto;
  border-radius:10px;
  border: 2px solid #F7D1CD;
  font-size: 120%;
  font-family: "Arial";
  font-weight: bold;
  display:flex;
  flex-direction: column;
  justify-content: center;
  margin-bottom: 1vh;
}
.image {
  background-color: #F7D1CD;
  height: 40%;
  display: flex;
  justify-content: center;
  align-content: center;

}
.desc {
  background-color: #F7D1CD;
  margin-top: 1vh;
  min-height: 30%;
  font-family: Arial;
  padding: 4px;
  font-weight: bold;
  color: #524459;
}
#footer{
  margin-bottom: 0;
  margin-top: 1vh;
  display: flex;
  flex-direction: row;
  width: available;
  flex-basis: available;
  justify-content: center;
  align-content: center;
  height: 35px;
}
#footer button {
  width: 35px;
  background-color: #735D78;
  color: #F7D1CD;
  border: none;
  border-radius: 4px;
  cursor: pointer;
}
#footer button:hover {
  width: 35px;
  background-color: #F7D1CD;
  color:#735D78 ;
  border: none;
  border-radius: 4px;
  cursor: pointer;
}
#footer .amt{
  display: flex;
  flex-direction: column;
  width: 80%;
  text-align: center;
  font-weight: bold;
  color: #524459;
  font-family: Arial;
  background-color: #F7D1CD;
  justify-content: center;
}
</style>