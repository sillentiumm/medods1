<template>
  <div id="app">
    <MainPage/>
  </div>
</template>

<script>
import MainPage from './components/MainPage.vue'

export default {
  name: 'App',
  components: {
    MainPage
  }
}
</script>

<style lang="sass">
*
  margin: 0
  padding: 0
  box-sizing: border-box
body
  min-height: 100vh
  background: #1F2128
</style>
