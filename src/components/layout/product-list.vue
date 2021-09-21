<template>
  <div>
    <h1>Product list </h1>
    <b-button variant="success" @click="getProducts">Test</b-button>
    <div class="row">
         <div v-for="item in products" :key="item.id" class="col-3" >
            <productItem :product="item" />
        </div>
    </div> 
  </div>
</template>

<script>
import productItem from "@/components/lists/product-list-item.vue";
export default {
  data() {
    return {
      products: [],
    };
  },
  components:{
      productItem,
  },
  methods: {
    getProducts() {
      fetch("https://fakestoreapi.com/products?limit=5")
        .then((res) => {
          return res.json();
        })
        .then((json) => {
          console.log(json);
          this.products = json;
        });
    },
  },
  mounted() {
    this.getProducts();
  },
};
</script>

<style lang="scss" scoped></style>