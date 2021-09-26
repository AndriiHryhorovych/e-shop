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
                alert("Товар додано " + product_id);
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
        text-decoration: none;
    }
}

.product-title {
    text-decoration-line: none !important;
    height: 42px;
    flex-grow: 0;
    margin: 37px 20px 25px;
    font-family: Roboto;
    font-size: 18px;
    font-weight: normal;
    font-stretch: normal;
    font-style: normal;
    line-height: normal;
    letter-spacing: normal;
    text-align: center;
    color: #000;
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