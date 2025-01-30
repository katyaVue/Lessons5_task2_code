<template>
  <div class="container">
    <div class="title">
      Корзина
    </div>
    <div class="card-item" v-for="item in cardItems" :key="item.title">
      <div class="card-item__title">
        {{item.title}}
      </div>
      <div class="card-item__price">
        {{ item.price}} грн.
      </div>
    </div>
    <div class="count"> Всього товарів на суму:{{ totalPrice }} грн.</div>

  </div>

</template>

<script>
export default {
  name: 'CardList',
  props: {
    cardItems: {
      type: Array,
      default: () => []
    }
  },
  computed: {
    totalPrice() {
      let sum = 0;
      for (let item of this.cardItems){
        sum = sum + item.price
      }
      return sum
    }
  }
}
</script>

<style scoped>
.count{
  margin-bottom: 100px;
}
.container{
  gap: 20px;
  padding: 40px;
  font-weight: 600;
  font-size: 24px;
  max-width: 600px;
}
.card-item{
  margin: 10px 0;
  padding: 10px;
  border: 1px solid #000;
}
</style>
