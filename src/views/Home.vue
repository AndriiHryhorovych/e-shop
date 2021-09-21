<template>
  <div class="home">
    <div class="container">
      <div class="row">
        <div class="col-12 carousel">
          <vue-carousel />
        </div>
        <productList />
      </div>
    </div>
  </div>
</template>

<script>
import VueCarousel from '../components/vue-carousel.vue';
import productList from '@/components/layout/product-list.vue';
// @ is an alias to /src


export default {
  name: 'Home',
  components: {
    VueCarousel,
    productList,
    
  },
  data(){
    return {

    };

  },
  methods:{
    
  },
  mounted() {

  }
}
</script>

<style lang="scss" scoped>
.carousel {
  padding: 60px 0 30px;
}

</style>
