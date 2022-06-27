<template>
    <div class="pt-3 d-flex">
        <select class="form-select" aria-label="Default select example" v-model="searchText">
            <option value="rock">rock</option>
            <option value="pop">pop</option>
            <option value="jazz">jazz</option>
            <option value="metal">metal</option>
        </select>
        <button type="button" class="btn btn-outline-secondary ms-2" @click="doResearch">cerca</button>
        <button type="button" class="btn btn-outline-secondary ms-2" @click="removeResearch">reset</button>
    </div>
</template>



<script>
export default {
    data(){
        return{
            searchText:""
        }
    },
    methods:{
        doResearch(){
            this.$emit("search", this.searchText)
        },
        removeResearch(){
            this.$emit("reset", this.searchText)
        }
    }
}
</script>


<style lang="scss" scoped>

.form-select{
    width: auto;
}

</style>