<template>
    <div class="disc text-center">
        <div class="disc-poster">
            <img class="img-fluid" :src="infoDisc.poster" :alt="infoDisc.title">
        </div>
        <div class="disc-title">
            <h4 class="text-white pt-2">{{infoDisc.title.toUpperCase()}}</h4>
        </div>
        <div class="disc-author text-muted">
            {{infoDisc.author}}
        </div>
        <div class="disc-year text-muted">
            {{infoDisc.year}}
        </div>
    </div>
</template>


<script>
export default {
    
    props:{
        infoDisc : Object
    },
}
</script>


<style lang="scss" scoped>
.disc{
    background-color: #2E3A46;
    height: 100%;
    padding: 1.2rem;
    width: 90%;
}
</style>