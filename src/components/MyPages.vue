<template>
    <div class="pagination">
        <div class="page-container">
            <div class="page"
                @click="setPage"
                v-for="(page, index) in tableData"
                :key="index"
                :id="index"
                :class="{
                    'current-page': currentPage === index
                }"
            >{{index+1}}</div>
        </div>
    </div>
</template>

<script>
    export default {
        data(){
            return{
                currentPage: 0
            }
        },
        props: ['tableData'],
        methods: {
            setPage(e){
                this.currentPage = Number(e.target.id)
                this.$emit('setPage', this.currentPage)
            }
        }
    }
</script>

<style scoped>

</style>