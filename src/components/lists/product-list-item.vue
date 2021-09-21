<template>
    <div class="product-item">
        <div class="thumb">
            <img :src="product.image" alt="">
        </div>
        <h4>
            <router-link :to="{ name: 'Product', params: { id: product.id } }  "  >
                {{product.title}}
            </router-link>
            </h4>
        <div class="price">
            <strong> {{ product.price }} </strong>
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
</style>