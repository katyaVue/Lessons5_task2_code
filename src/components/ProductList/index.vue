<template>
  <div class="wrapper">
    <product-item
        v-for="item in itemsData"
        :key="item.id"
        :item-data="item"
        :card="card"
        @buyProduct="$emit('buyProduct', item.id)"
    />
  </div>

</template>

<script>
import ProductItem from './ProductItem.vue'

export default {
  name: 'ProductList',
  components: {
    ProductItem
  },
  props: {
    itemsData: {
      type: Array,
      default: () => []
    },
    card:{
      type: Array,
      default: () => []
    }
  }
}

</script>

<style lang="css" scoped>
.wrapper {
  background: #e7cccc;
  padding: 40px 0 0 40px;
  max-width: 800px;
}
</style>