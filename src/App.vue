<template>
  <div>
    <product-list :items-data="productItemsList" :card="card" @buyProduct="onBuy"/>
    <card-list  :card-items="card"/>
  </div>
</template>

<script>
import ProductList from "./components/ProductList";
import {notebooksList} from "./constants/3_data_notebooks"
import CardList from "./components/CardList";

export default {
  name: "App",
  components: {CardList, ProductList},
  data() {
    return {
      card: [],
    }
  },
  computed: {
    productItemsList() {
      return notebooksList
    },
  },
  methods:{
    getItemById(itemId) {
      return this.productItemsList.find((item) => item.id === itemId)
    },
    onBuy(itemId) {
      const item = this.getItemById(itemId)
      if (item && !this.card.some(cartItem => cartItem.id === item.id)) {
        this.card.push(item)
      }
    },
  }
};
</script>

<style>
body{
  background: #e7cccc;
}
</style>
