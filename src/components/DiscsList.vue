<template>
    <section class="container">
        <div class="pt-5">
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

export default {
    components:{
    DiscCard,
},
    data(){
        return{
            apiUrl: "https://flynn.boolean.careers/exercises/api/array/music",
            discsList :[],

        }
    },
    methods:{
        fetchDiscsList(){
            axios.get(this.apiUrl).then(resp =>{
                this.discsList = resp.data.response
                
            })
        }
    },
    mounted(){
        this.fetchDiscsList()
    }
}
</script>


<style lang="scss" scoped>

</style>