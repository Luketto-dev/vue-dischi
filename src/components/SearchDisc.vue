<template>
    <div class="pt-3 d-flex">
        <select class="form-select" aria-label="Default select example" v-model="genre" >
            <option value="">filtra per genere</option>
            <option v-for="(genere,i ) in listaGeneri" :key="i" :value="genere">{{genere}} </option>
        </select>
        <button type="button" class="btn btn-outline-secondary ms-2" @click="onSearchClick">cerca</button>
    </div>
</template>



<script>
export default {
    props:{
        listaGeneri: Array
    },
    data(){
        return{
            genre:""
        }
    },
    methods:{
        onSearchClick(){
            
            this.$emit("searchGenre", this.genre)
            
        },
        
    }
}
</script>


<style lang="scss" scoped>

.form-select{
    width: auto;
}

</style>