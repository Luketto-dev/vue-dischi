<template>
    <section class="container">
        <div class="alert alert info text-white">
            artista attivo : {{artist}}
        </div>
        <div>
            <SearchDisc :listaGeneri="this.getListaGeneri()" @searchGenre="onSearchGenre"></SearchDisc> <!-- @search="getFilteredDisc" @reset="onSearchReset" -->
        </div>
        <div class="py-5">
            <div class="row row-cols-5 gy-3 gx-2">
                <div class="col flex-shrink-0" v-for="disc in getFliteredGenre" :key="disc.title">
                    <DiscCard :infoDisc="disc"></DiscCard>
                </div>
            </div>
        </div>
    </section>
</template>


<script>
import axios from "axios";
import DiscCard from "./DiscCard.vue";
import SearchDisc from "./SearchDisc.vue";


export default {
    components:{
    DiscCard,
    SearchDisc,
    },
    props:{
        artist: String,
    },
    data(){
        return{
            apiUrl: "https://flynn.boolean.careers/exercises/api/array/music",
            discsList :[],
            genre: "",
        }
    },
    computed:{
        getFliteredGenre(){
            if (!this.genre) {
                return this.discsList
            }
            return this.discsList.filter((album) =>{
                return album.genre === this.genre
            })
        },
        getFilteredArtist(){
            if (!this.artist) {
                return this.discsList
            }
            return this.discsList.filter((album) => {
                return album.author === this.artist
            })
        }
    },
    methods:{
        fetchDiscsList(){
            axios.get(this.apiUrl).then(resp =>{
                this.discsList = resp.data.response

                this.$emit("artistsUpdate", this.getListaArtisti())
            })
        },
        getListaGeneri(){
            const listaGeneri = []
            
            this.discsList.forEach(album => {
                // il genere che sto andando analizzando in questo ciclo esiste gia nella mia lista finale
                // se non esiste lo pusho 
                if (!listaGeneri.includes(album.genre)) {
                    listaGeneri.push(album.genre)
                }
                
            });
            return listaGeneri
        },
        getListaArtisti(){
            const listaArtisti = [];
            this.discsList.forEach(disco => {
                if (!listaArtisti.includes(disco.author)) {
                    listaArtisti.push(disco.author)
                }
            })

            return listaArtisti
        },
        onSearchGenre(genre){
            this.genre = genre
        },
        
    },
    mounted(){
        this.fetchDiscsList()
    }
}
</script>


<style lang="scss" scoped>

</style>