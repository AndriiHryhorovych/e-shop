<template>
<div>
    <div v-if="3<2"  class="cart-empty">
        <div class="container">
            <div class="row">
                <div class="col-12 d-flex flex-column justify-content-center align-items-center">
                    <div class="cart-title">
                        Кошик замовлень
                    </div>
                    <div class="cart-info">
                        На жаль, Ви ще нічого не додали до кошика
                    </div>
                    <div id="button-to-catalog">
                        <b-button href="/catalog/all">До каталогу</b-button>
                    </div>   
                </div>
            </div>
        </div>
    </div>
    <div v-else class="cart-full">
        <div class="container">
            <div class="row">
                <div class="col-12 title">
                    <span>Кошик замовлень</span>
                </div>
            </div>
            <div class="row product-in-cart">
                <div class="col-2 d-flex justify-content-center align-items-center">
                    <img :src="product.image" alt="рисунок">
                </div>
                <div class="col-8 d-flex align-items-center">
                    <span>{{product.title}}</span>
                </div>
                <div class="col-2 price d-flex justify-content-center align-items-center">
                    {{product.price}} USD
                </div>
            </div>
            <div class="row button-to-order d-flex justify-content-center align-items-center">
                <div class="col-4">
                </div>
                <div class="col-4 d-flex justify-content-center align-items-center">
                    <b-button href="#">Оформити замовлення</b-button>
                </div>
                <div class="col-4">
                </div>
            </div>
            <div class="row">
                <div class="col-12 product-other">
                    <span>Вас також можуть зацікавити</span>
                </div>
            </div>
            <div class="row">
                <div v-for="item in products" :key="item.id" class="col-3" >
                    <productItem :product="item" />
                </div>
            </div>
        </div>
    </div>
</div>
</template>

<script>
// import productList from '@/components/layout/product-list.vue';
import productItem from "@/components/lists/product-list-item.vue";
export default {
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
            var id=5; //window.localStorage.id;
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
        // console.log(this.product.category)
            fetch("https://fakestoreapi.com/products/category/" + this.product.category + "?limit=4")
        .then((res) => {
            return res.json();
        })
        .then(json => {
            this.products = json;
        });
        }
    },
    mounted() {
        this.getProduct();
    }
}
</script>

<style lang="scss" scoped>
.cart-empty {
    min-height: calc(100vh - 151px);
    .cart-title{
        margin: 41px 0 23px 0;
        font-family: Roboto;
        font-size: 36px;
        font-weight: 500;
        font-stretch: normal;
        font-style: normal;
        line-height: normal;
        letter-spacing: normal;
        text-align: center;
        color: #000;
    }
    .cart-info {
        width: 542px;
        height: 54px;
        flex-grow: 0;
        margin: 23px 0 33px 0;
        padding: 12px 0 16px;
        border-radius: 6px;
        background-color: rgba(255, 168, 0, 0.21);
        font-family: Roboto;
        font-size: 22px;
        font-weight: 500;
        font-stretch: normal;
        font-style: normal;
        line-height: normal;
        letter-spacing: normal;
        text-align: center;
        color: #ff842c;
    }
    .btn {
        height: 56px;
        width: 178px;
        flex-grow: 0;
        margin: 33px 0;
        padding: 15px 0;
        border-radius: 6px;
        border-color: #ff842c;
        box-shadow: 0 4px 8px 0 rgba(0, 0, 0, 0.15);
        background-color: #ff842c;
        font-family: Roboto;
        font-size: 22px;
        font-weight: 500;
        font-stretch: normal;
        font-style: normal;
        line-height: normal;
        letter-spacing: normal;
        text-align: center;
        color: #fff;
        transition: 0.3s;
    }
    .btn:hover {
        border-color: gray;
        background-color: gray;
        transition: 0.3s;
    }

.button-to-catalog {
    text-align: center;
}
}
.cart-full {
    .title{
        margin: 41px 0 39px;
        font-family: Roboto;
        font-size: 36px;
        font-weight: 500;
        font-stretch: normal;
        font-style: normal;
        line-height: normal;
        letter-spacing: normal;
        text-align: center;
        color: #000;
    }
    .product-in-cart {
        width: 100%;
        height: 193px;
        flex-grow: 0;
        margin: 39px 0 31px;
        padding: 14px 43px 15px 10px;
        border-radius: 6px;
        background-color: #f5f5f5;
        img {
            max-height: 157px;
            padding: 18px 32px;
            background-color: #fff;
        }
        span {
            font-family: Roboto;
            font-size: 24px;
            font-weight: bold;
            font-stretch: normal;
            font-style: normal;
            line-height: normal;
            letter-spacing: normal;
            text-align: left;
            color: #000;
        }
        .price {
            font-family: Roboto;
            font-size: 28px;
            font-weight: 500;
            font-stretch: normal;
            font-style: normal;
            line-height: normal;
            letter-spacing: normal;
            text-align: right;
            color: #009d35;
        }
    }
    .button-to-order {
        text-align: center;
           
        .btn {
            width: 100%;
            height: 56px;
            flex-grow: 0;
            margin: 18px 0 111px 0;
            padding: 15px 77px 15px 75px;
            border-radius: 6px;
            box-shadow: 0 4px 8px 0 rgba(0, 0, 0, 0.15);
            background-color: #ff842c !important;
            border-color: #ff842c !important;
            transition: 0.3s;
            flex-grow: 0;
            font-family: Roboto;
            font-size: 22px;
            font-weight: 500;
            font-stretch: normal;
            font-style: normal;
            line-height: normal;
            letter-spacing: normal;
            text-align: center;
            color: #fff;
        }
        .btn:hover {
            background-color: gray !important;
            border-color: gray !important;
            transition: 0.3s;
        }
    }
    .product-other {
        margin: 0 0 75px 1px;
  font-family: Roboto;
  font-size: 32px;
  font-weight: normal;
  font-stretch: normal;
  font-style: normal;
  line-height: normal;
  letter-spacing: normal;
  text-align: left;
  color: #000;
    }

    
}
</style>