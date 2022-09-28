<template>
  <div class="main">
    <div id="inner_box">
      Order has been placed!
      <button @click="newOrder">Place another order</button>
    </div>
  </div>
</template>

<script setup>
import {defineEmits} from "vue";

const emits = defineEmits('newOrder');
function newOrder() {
  emits('newOrder');
}
</script>

<style scoped>
.main{
  background-color: #D1B3C4;
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
  height: 100vh;
  width: 100vw;
}
#inner_box {
  background-color: #B392AC;
  border: solid 5px #F7D1CD;
  border-radius: 20px;
  color: #735D78;
  font-weight: bold;
  font-size: 200% ;
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
  text-align: center;
  width: 40%;
  height: 20%;
}
button{
  width: 20%;
  margin-top: 5vh;
  height: 30%;
  border-radius: 3vh;
  background-color: #735D78;
  border: solid 5px #F7D1CD;
  color: #F7D1CD;
}
</style>