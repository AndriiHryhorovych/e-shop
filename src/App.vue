<template>
  <div id="app">
    <appHeader />
    <router-view/>
    <appFooter />
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
