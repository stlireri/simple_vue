<template>
<div>
  <input type="text" v-model="item.name" placeholder="Enter the items name"/>
  <br>
  <input type="text" v-model="item.price" placeholder="Enter the item price"/>
  <br>
  <input type="button" @click="AddItem" value="Add To Cart"/>
  <hr>
  <div v-bind="item in items">
    {{item.name}}
    {{item.price}}
  </div>
  <hr>
  <h3>Total Price of items</h3>
 <p>{{totalPrice}}</p>

</div>
</template>

<script>
export default {
  data(){
    return {
      item: {},
      items: [],
    }
  }, methods: {
    AddItem(){
      this.items.push({name:this.item.name, price:this.item.price});
      this.item = {};
    }
  },computed: {
   totalPrice(){
     var total = 0;
     this.items.forEach((item) => {
       total+=parseInt(item.price);
     });
     return total;
   },
  }, 
};
</script>




