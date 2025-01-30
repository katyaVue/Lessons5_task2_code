<template>
    <div class="item">
      <div class="item__photo">
        <div class="img">
          <img :src="itemData.imgSrc" alt="">
        </div>
      </div>
      <div class="item__info">
        <div class="title">
          {{ itemData.title}}
        </div>
        <div class="price">
          <a :href="itemData.link">
            {{ itemData.price }} грн.
          </a>
          <div class="btn" v-if="!isInCart" @click="$emit('buyProduct', itemData.id)">Купити</div>
          <div class="btn" v-else @click="$emit('deleteProduct', itemData.id)">Видалити з корзини</div>
        </div>
      </div>
    </div>
</template>

<script>
export default {
  name: 'ProductItem',
  props: {
    itemData: {
      type: Object,
      default: () => ({})
    },
    card: {
      type: Array,
      default: () => []
    }
  },
  computed: {
    isInCart() {
      return this.card.some(cartItem => cartItem.id === this.itemData.id);
    }
  }
}
</script>
<style lang="css" scoped>

.item {
  display: flex;
  gap: 20px;
  margin-bottom: 20px;

  .img {
    width: 100%;
    height: 100px;
    border-radius: 50%;
    margin-bottom: 10px;

    img {
      width: 100%;
      height: 100%;
      object-fit: cover;
      border-radius: 10%;
    }
  }
}
.title{
  font-weight: 600;
  margin-bottom: 10px;
  font-size: 20px;
}
.item__info{
  width: 400px;
}
.item__photo{
  width: 100px;
}
  .price, .description {
    color: #fff;
    padding-left: 5px;
    margin: 0;
  }

  .btn {
    color: green;
    font-weight: 600;
    font-size: 20px;
  }

  .price {
    display: flex;
    justify-content: space-between;

    .logo {
      width: 15px;
      height: 15px;
      min-width: 15px;
      margin-right: 10px;
    }
  }

.price{
  font-size: 20px;
  font-weight: 600;
}


</style>