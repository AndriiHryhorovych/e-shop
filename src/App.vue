<template>
  <div id="app">
    <appHeader />
    <router-view/>
    <appFooter />

    <div>
      <b-modal id="bv-modal-example" hide-footer>
        <div class="d-block text-center">
          <div class="Circle">
            <img src="assets/carbon.svg">
          </div>
          <h3>Товар в кошику</h3>
        </div>
        <b-button class="mt-3" block @click="$bvModal.hide('bv-modal-example')">Закрити</b-button>
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

</style>
