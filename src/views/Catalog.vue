<template>
    <div>
        <div class="container">
            <div class="row">
                <div class="col-3">
                    <div class="category">
                        <div class="category-title">
                            Товари за категоріями
                        </div> 
                        <ul class="catalog-categories">
                            <li>
                                <router-link :to="{name: 'Catalog', params: {category: 'all'}}">
                                    Всі товари
                                </router-link>
                            </li>
                            <li v-for="(c, i) in categories" :key = "c + i">
                                <router-link :to="{name: 'Catalog', params: {category: c}}">
                                    {{c}}
                                </router-link>
                            </li>
                        </ul>   
                    </div>
                </div>
                <div class="col-9">
                    <div v-for="item in products" :key="item.id" class="col-3" >
                        <productItem :product="item" />
                    </div>
                </div>
            </div>
        </div>
    </div>
</template>

<script>
import productItem from "@/components/lists/product-list-item.vue";
export default {
    data () {
       return {
           isLoading: false,
           categories: [],
           products: [],
       };     
    },
    computed: {
        currentCategory() {
            return this.$route.params.category;
        },
    },
    components: {
        productItem,
    },
    watch: {
        currentCategory: {
            handler() {
                if (this.currentCategory == "all") {
                    this.getProducts();
                } else {
                    this.getProductByCategory();
                }
            },
        },
    },
    methods: {
        getCategories() {
            fetch("https://fakestoreapi.com/products/categories")
                .then((res) => {
                    return res.json();
                })
                .then((json) => {
                    this.categories = json;
            });
        },
        getProducts() {
            fetch('https://fakestoreapi.com/products?limit=9')
            .then((res) => {
                return res.json ();
            })
            .then((json) => {
                this.products = json
            });
        },
        getProductByCategory() {
            fetch("https://fakestoreapi.com/products/category/" + this.currentCategory)
            .then((res) => {
            return res.json();
            })
            .then(json => {
                this.products = json;
            });
        }
    },
    mounted () {
        this.getCategories();
        if (this.currentCategory == "all") {
            this.getProducts();
        } else {
            this.getProductByCategory();
        }
    },
};


</script>

<style lang="scss" scoped>
.category-title {
    margin:  77px 0 8px 0;
  font-family: Roboto;
  font-size: 18px;
  font-weight: normal;
  font-stretch: normal;
  font-style: normal;
  line-height: normal;
  letter-spacing: normal;
  text-align: left;
  color: #000;
}

</style>