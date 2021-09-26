<template>
    <div class="product">
        <div class="container">
            <div class="row product d-flex">
                <div class="col-4 product-image">
                    <img :src="product.image" alt="">
                </div>
                <div class="col-8 product-title">
                    <h1> {{product.title}} </h1>
                    <div class="price">
                        <span>{{product.price}} USD</span>
                    </div>
                    <div id="button-to-cart">
                        <b-button @click="addToCart(product.id)">До кошика</b-button>
                    </div>  

                </div>
            </div>
            <div class="product_more-title">
                Ще товари тієї ж категорії
            </div>
            <!-- <productList /> -->
            <div class="row">
                <div v-for="item in products" :key="item.id" class="col-3" >
                    <productItem :product="item" />
                </div>
            </div> 
        </div> 

    </div>
</template>

<script>
    // import productList from '@/components/layout/product-list.vue';
    import productItem from "@/components/lists/product-list-item.vue";

    export default {
        // props: ['product'],
        components: {
            // productList,
            productItem,
    
        },
        data () {
            return {
                product: {},
                products: [],
            };
        },
        methods: {
            getProduct (){
                var id= this.$route.params.id;
                fetch("https://fakestoreapi.com/products/"+id)
                .then(res=> {
                    return res.json()
                })
                .then(json=> {
                    console.log(json);
                    this.product = json;
                    this.getProductByCategory();
                })
            },
            getProductByCategory () {
                fetch("https://fakestoreapi.com/products/category/" + this.product.category + "?limit=4")
                .then((res) => {
                    return res.json();
                })
                .then(json => {
                    this.products = json;
                });
            },
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
        mounted() {
            this.getProduct();
        }
    }
</script>

<style lang="scss" scoped>
.product {
    margin-top: 60px;
}
.product-image {
    margin: 108px 0 147px 0;
    img {
        max-width: 100%;
        height: 372px;
    }
}
.product-title {
    margin: 80px 0 18px;
    font-family: Roboto;
    font-size: 32px;
    font-weight: bold;
    font-stretch: normal;
    font-style: normal;
    line-height: normal;
    letter-spacing: normal;
    text-align: left;
    color: #000;
   .price {
        margin: 18px 0 18px 0;
        font-family: Roboto;
        font-size: 28px;
        font-weight: 500;
        font-stretch: normal;
        font-style: normal;
        line-height: normal;
        letter-spacing: normal;
        text-align: left;
        color: #009d35;
    }
    .btn {
        width: 377px;
        height: 56px;
        flex-grow: 0;
        margin: 18px 0 0 0;
        padding: 15px 77px 15px 75px;
        border-radius: 6px;
        box-shadow: 0 4px 8px 0 rgba(0, 0, 0, 0.15);
        background-color: #ff842c;
        border-color: #ff842c;
        transition: 0.3s;
    }
    .btn:hover {
        background-color: gray;
        border-color: gray;
        transition: 0.3s;
    }
}
.product_more-title {
    margin: 0 0 57px 3px;
  font-family: Roboto;
  font-size: 32px;
  font-weight: normal;
  font-stretch: normal;
  font-style: normal;
  line-height: normal;
  letter-spacing: normal;
  text-align: start;
  color: #000;
}
 
</style>