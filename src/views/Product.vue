<template>
    <div>
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
                        <b-button href="/cart">До кошика</b-button>
                    </div>  

                </div>
            </div>
            <div class="product_more-title">
                Ще товари тієї ж категорії
            </div>
            <productList />
        </div> 

    </div>
</template>

<script>
    import productList from '@/components/layout/product-list.vue';

    export default {
        components: {
            productList,
    
        },
        data () {
            return {
                product: {},
            };
        },
        methods: {
            getProduct(){
                var id= this.$route.params.id;
                fetch("https://fakestoreapi.com/products/"+id)
            .then(res=> {
                return res.json()
            })
            .then(json=> {
                console.log(json);
                this.product = json;
            })
            },
        },
        mounted() {
            this.getProduct();
        }
    }
</script>

<style lang="scss" scoped>
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