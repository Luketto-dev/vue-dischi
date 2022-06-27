<template>
    <section class="container">
        <div>
            <SearchDisc @search="getFilteredDisc" @reset="onSearchReset"></SearchDisc>
        </div>
        <div class="py-5">
            <div class="row row-cols-5 gy-3 gx-2">
                <div class="col flex-shrink-0" v-for="disc in discsList" :key="disc.title">
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
    data(){
        return{
            apiUrl: "https://flynn.boolean.careers/exercises/api/array/music",
            discsList :[],

        }
    },
    computed:{
        
    },
    methods:{
        fetchDiscsList(){
            axios.get(this.apiUrl).then(resp =>{
                this.discsList = resp.data.response
                
            })
        },
        getFilteredDisc(searchText){
            this.discsList = this.discsList.filter(disc => {
                if (disc.genre.toLowerCase().includes(searchText.toLowerCase())) {
                    return this.discsList
                }      
            })

        },
        onSearchReset(){
            this.fetchDiscsList()

        }
    },
    mounted(){
        this.fetchDiscsList()
    }
}
</script>


<style lang="scss" scoped>

</style>