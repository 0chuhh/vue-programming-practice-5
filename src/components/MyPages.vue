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
.pagination{

  background: #ffff;
  height: 42px;
  border-radius: 17px;
  border: 1px solid #CB3F3F;
  display: inline-block;

}
.page-container{
  height: 100%;
  display: flex;
  align-items: center;
  justify-content: space-between;
}
.page{
  position: relative;
  height: 100%;
  width:65px;
  display: flex;
  justify-content: center;
  align-items: center;
  cursor: pointer;
}

.page::before{
content: '';
background: #CB3F3F;
width: 1px;
height: 100%;
position: absolute;
top:0;
right:0;
}
.page:last-child::before{
  display: none;
}
.current-page{
  background: #CB3F3F;

}
.current-page:first-child{
  border-top-left-radius: 17px;
  border-bottom-left-radius: 17px;
}
.current-page:last-child{
  border-top-right-radius: 17px;
  border-bottom-right-radius: 17px;
}
</style>