<template>
    <header class="py-2 px-3 d-flex">
        <div class="header-logo">
            <img src="/img/logo-small.svg" alt="">
        </div>
        <SearchDiscArtist :lista-artisti="listaArtisti" @searchArtist="$emit('searchArtist', $event)" class="ms-auto"></SearchDiscArtist>
    </header>
</template>


<script>
import SearchDiscArtist from "./SearchDiscArtist.vue";

export default {
    components:{
        SearchDiscArtist,
    },
    props:{
        listaArtisti: Array
    }
}
</script>

<style lang="scss" scoped>

header{
    background-color:#2E3A46;
    & .header-logo img{
        width: 30px;
        color:#1ED65F
    }
}

</style>