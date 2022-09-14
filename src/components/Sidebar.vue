<template>
<div id = "main">
  <button>All</button>
  <button>Drinks</button>
  <button>Dessert</button>
  <div id="order">
    <div id="orderHeader">Items</div>
    <div v-for="item in itemList" :key="item.name">{{item.name}}&ensp;{{item.value}}</div>
  </div>
</div>
</template>

<script>

export default {
  name: "Side-bar",
  props: {
    orders:[]
  },
  computed:{
    itemList(){
      if(!this.orders){
        console.log("computing item list")
        console.log(this.orders)
        return[];
      }else{
        var items = [];
        // eslint-disable-next-line vue/no-mutating-props
        var sorted = Array.from(this.orders).sort();
        while(sorted.length >0) {
          const item = sorted.pop();
          console.log(item);
          var found = false;
          items.forEach(entry => {
            if(entry.name == item) {
              entry.value++;
              found = true;
            }
          });
          if(!found) {
            items.push({name:item, value:1});
          }
        }
        return items;
      }
    }
  },
  watch:{

  }
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
#order{
  border: 2px solid #524459;
  min-height: 40%;
  margin: 0;
  min-width: 85%;
  padding: 10px;
  border-radius: 5px;
}
#orderHeader{
  border-bottom: 4px solid #524459;
  width: 100%;
  font-weight: bold;
  color: #F7D1CD;
}
</style>