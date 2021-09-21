<template>
    <div class="product-item">
        <div class="thumb">
            <img :src="product.image" alt="">
        </div>
            <router-link :to="{ name: 'Product', params: { id: product.id } }  "  >
                {{product.title}}
            </router-link>
        <div class="price">
            <strong> {{ product.price }} USD</strong>
        </div>
    </div>
</template>

<script>
    export default {
        props:['product']
    }
</script>

<style lang="scss" scoped>
.thumb {
    text-align: center;
    img {
        max-width: 100%;
        height: 140px;
    }
}
.price {
    text-align: center;
    font-family: Roboto;
  font-size: 22px;
  font-weight: 500;
  font-stretch: normal;
  font-style: normal;
  line-height: normal;
  letter-spacing: normal;
  text-align: center;
  color: #009d35;
}
</style>