<template>
  <div id="app">
    <TheHeader :lista-artisti="listaArtisti" @searchArtist="onSearchArtist"></TheHeader>
    <main class="py-3">
      <DiscsList @artistsUpdate="onArtistsUpdate" :artist="artist" ></DiscsList>
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
  },
  data(){
    return{
      listaArtisti: [],
      artist : ""
    }
  },
  methods : {
    onArtistsUpdate(listaArtisti){
      this.listaArtisti = listaArtisti
      
    },
    onSearchArtist(artist){
      this.artist = artist
      
    }
  }
}
</script>

<style lang="scss">
@import "./assets/scss/main.scss";

</style>
