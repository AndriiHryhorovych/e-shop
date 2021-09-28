<template>
    <div class="product-item">
        <div class="thumb">
            <router-link class="link" :to="{ name: 'Product', params: { id: product.id, productCategory: product.category } } "  >
                <img :src="product.image" alt="">
                <br>
                <div class="product-title">
                    {{product.title}}
                </div>
            </router-link>
        </div>
        <div class="price">
            <strong> {{ product.price }} USD</strong>
        </div>
        <div class="button-to-cart">
            <b-button @click="addToCart(product.id)">До кошика</b-button>
        </div>
    </div>
</template>

<script>
    export default {
        props:['product'],
        methods: {
            addToCart(product_id) {
                var item = {
                    count: 1,
                    id: product_id,
                };
                window.localStorage.setItem("cart",JSON.stringify(item));
                this.$bvModal.show("bv-modal-example");
            },
        },
    };
</script>

<style lang="scss" scoped>
.thumb {
    text-align: center;
    img {
        max-width: 100%;
        height: 140px;
    }
    link {
        text-decoration: none !important;
    }
    a {
        text-decoration: none !important;
    }
}

.product-title {
    text-decoration-line: none !important;
    height: 42px;
    flex-grow: 0;
    margin: 37px 20px 15px;
    font-family: Roboto;
    font-size: 18px;
    font-weight: normal;
    font-stretch: normal;
    font-style: normal;
    line-height: normal;
    letter-spacing: normal;
    text-align: center;
    color: #000;
    -ms-text-overflow: ellipsis;
    -o-text-overflow: ellipsis;
    text-overflow: ellipsis;
    overflow: hidden;
    -ms-line-clamp: 2;
    -webkit-line-clamp: 2;
    line-clamp: 2;
    display: -webkit-box;
    display: box;
    word-wrap: break-word;
    -webkit-box-orient: vertical;
    box-orient: vertical;
  a {
      text-decoration: none !important;
  }
}
.price {
    text-decoration: none;
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
.button-to-cart {
    text-align: center;
    .btn {
        height: 56px;
        width: 191px;
        flex-grow: 0;
        margin: 13px 46px 70px 46px;
        padding: 15px 39px 15px 38px;
        border-radius: 6px;
        box-shadow: 0 4px 8px 0 rgba(0, 0, 0, 0.15);
        background-color: #ff842c;
        border-color: #ff842c;
        transition: 0.3s;   
    }
    .btn:hover{
        background-color: gray !important;
        border-color: gray;
        transition: 0.3s;
    }
}
</style>