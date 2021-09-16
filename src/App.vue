<template>
  <div id="app">
    <Head/>
    <router-view/>
  </div>
</template>

<script>
import Head from './components/head.vue'
export default {
  components: {
    Head
  },
  setup () {
    return {

    }
  }
}
</script>

<style lang="scss">
#app{
  font-family: 'Nunito', 'Noto Sans TC', sans-serif;
  background-color: #FFFBEB;
  min-height: 100vh;
}
</style>
