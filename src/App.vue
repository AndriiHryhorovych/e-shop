<template>
  <div id="app">
    <appHeader />
    <router-view/>
    <appFooter />

    <div>
      <b-modal  id="bv-modal-example" centered hide-footer hide-header>
        <div class="d-block text-center">
          <div class="Circle">
            <img src="@/assets/carbon.svg">
          </div>
          <span class="messege">Товар в кошику</span>
          <b-button class="mt-3" block @click="$bvModal.hide('bv-modal-example')">Закрити</b-button>
        </div>
        
      </b-modal>
    </div>

  </div>
</template>

<script>
import appFooter from '@/components/appFooter.vue'
import appHeader from '@/components/appHeader.vue'

export default {
  name: 'app',
  components: {
    appFooter,
    appHeader,
  },

}


</script>


<style lang="scss">
@import url('https://fonts.googleapis.com/css2?family=Roboto:ital,wght@0,400;0,700;1,400;1,700&display=swap');
.messege{
  font-family: Roboto;
  font-size: 24px;
  font-weight: normal;
  font-stretch: normal;
  font-style: normal;
  line-height: normal;
  letter-spacing: normal;
  text-align: center;
  color: #000;
}
.mt-3 {
  width: calc(100% - 18px);
  height: 58px;
  background-color: #ff842c !important;
  border-color: #ff842c !important;
  transition: 0.3s;  
} 
  .mt-3:hover{
      background-color: gray !important;
      border-color: gray !important;
      transition: 0.3s;
  }



</style>
