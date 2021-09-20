<template>
    <div>
      <carousel :per-page="1" :navigate-to="someLocalProperty" :mouse-drag="true">
        <slide class="carousel-slide">
          <img src="@/assets/Slide.png" alt="Slide 1 Content">
        </slide>
        <slide class="carousel-slide">
          <img src="@/assets/Slide.png" alt="Slide 2 Content">
        </slide>
        <slide class="carousel-slide">
          <img src="@/assets/Slide.png" alt="Slide 3 Content">
        </slide>
  </carousel>
    </div>
</template>



<script>
import { Carousel, Slide } from 'vue-carousel';
 
export default {
 
  components: {
    Carousel,
    Slide
  }
 
};

</script>

<style lang="scss" scoped>
.carousel-slide img{
  width: 100%;
  box-shadow: 0 0 20px 0 rgba(0, 0, 0, 0.15);
  margin: 0 0 20px;
}
</style>