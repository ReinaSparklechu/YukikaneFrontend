<template>
<div id = "main">
  <button>All</button>
  <button>Drinks</button>
  <button>Dessert</button>
  <div id="order">
    <div id="orderHeader">Items</div>
    <div class="items" v-for="item in itemList" :key="item.name">{{item.name}}&ensp;{{item.value}}</div>
  </div>
  <button @click ="sendOrder">Submit Order!</button>
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

  },
  methods: {
    sendOrder() {
      this.$emit('sendOrder');
    }
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
  height: 5vh;
  margin: 20px;
  border: 4px solid indigo;
  background-color: aliceblue;
  border-radius: 20px;
}
button:hover{
  border-radius: 5px;
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
.items {
  display: flex;
  justify-content: space-between;
  text-align: justify-all;
  border-bottom: 2px solid #F7D1CD;
  font-weight: bold;
  margin-top: 2px;
  width: 100%;
}
</style>