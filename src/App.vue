<template>
  <div id="app">
    <TheHeader></TheHeader>
    <main class="py-3">
      <DiscsList></DiscsList>
    </main>
    
  </div>
</template>

<script>
import TheHeader from './components/TheHeader.vue'
import DiscsList from './components/DiscsList.vue'


export default {
  name: 'App',
  components: {
    TheHeader,
    DiscsList,
  }
}
</script>

<style lang="scss">
@import "./assets/scss/main.scss";

</style>
