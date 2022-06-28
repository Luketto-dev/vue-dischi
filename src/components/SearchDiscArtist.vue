<template>
    <div class="d.flex">
        <div class="input-group">
            <select class="form-select" name="" id="" v-model="artist">
                <option value="">filtra per artista</option>
                <option v-for="(artista, i) in listaArtisti" :key="i" :value="artista">{{artista}}</option>

            </select>
            <button class="btn btn-outline-secondary ms-2" @click="onSearchArtistClick">cerca</button>
        </div>
    </div>
</template>


<script>
export default {
    data(){
        return{
            artist: ""
        }
    },
    props:{
        listaArtisti: Array,
    },
    methods:{
        onSearchArtistClick(){
            this.$emit("searchArtist", this.artist)
        }
    }
}
</script>


<style lang="scss" scoped>

</style>