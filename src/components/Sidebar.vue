<template>
<div id = "main">
  <button>All</button>
  <button>Drinks</button>
  <button>Dessert</button>
</div>
</template>

<script>
export default {
  name: "Side-bar"
}
</script>

<style scoped>
*{
  width: 10vh;
  margin: 0;
}
#main{
  margin: 0;
  width: 10vw;
  background-color: mediumpurple;
  display: flex;
  height: 100vh;
  flex-direction: column;
  justify-content: flex-start;
  align-items: center;
}
button{
  font-family: "Arial";
  font-size: large;
  font-weight: bold;
  color: mediumpurple;
  width: 15vh;
  height: 15vh;
  margin: 20px;
  border: 4px solid indigo;
  background-color: aliceblue;
  border-radius: 30%;
}
button:hover{
  border-radius: 20px;
}
</style>