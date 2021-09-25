<template>
    <div>
        <div class="container">
            <div class="row">
                <div class="col-3">
                    <div class="category">
                        <div class="category-title">
                            Товари за категоріями
                        </div> 
                        <div class="line-1">
                        </div>
                        <ul class="catalog-categories">
                            <li>
                                <router-link :to="{name: 'Catalog', params: {category: 'all'}}">
                                    <strong>Всі товари</strong>
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
                
                <div class="col-9 d-flex flex-wrap">
                    <div v-if=" this.currentCategory == 'all' "  class="current-category col-9">
                        Всі товари
                    </div> 
                    <div v-else class="current-category col-9">
                        {{this.currentCategory}} 
                    </div>             
                    <div v-for="item in products" :key="item.id" class="col-4" >
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
.line-1 {
  width: 100%;
  height: 1px;
  flex-grow: 0;
  margin: 8px 0 15px;
  background-color: #000;
}
.catalog-categories {
    list-style-type: none;
    
    margin-left: -30px;
    a {
        text-decoration: none;
        font-family: Roboto;
        font-size: 18px;
        font-weight: normal;
        font-stretch: normal;
        font-style: normal;
        line-height: 1.9;
        letter-spacing: normal;
        text-align: left;
        color: #000;
        padding-bottom: 15px;
        transition: 0.5s;
    }
    a:hover{
        font-weight: 900;
        transition: 0.5s;
    }
    
}
.current-category {
    margin: 69px 0;
  font-family: Roboto;
  font-size: 36px;
  font-weight: normal;
  font-stretch: normal;
  font-style: normal;
  line-height: normal;
  letter-spacing: normal;
  text-align: left;
  color: #000;
}

</style>