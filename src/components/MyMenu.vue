<template>


  <div class="container">
  
  <div class="table-logo">
    <img src="/assets/menu-logo.png" alt="">
  </div>

  <my-search
    @search="search"
    :value="value"
  >
  </my-search>

  <my-table
    @remove="removeRow"
    :tableData="tableData"
    :tableHeader="tableHeader"
    :currentPage="currentPage"
  />
  <div class="end-section">
    <my-pages
    :currentPage="currentPage"
    :tableData="tableData"
    @setPage="setPage"
  />
  <div @click="showPopupToggle" class="add-button">Добавить</div>

  </div>
  <my-popup
  v-if="showPopup"
  :tableHeader="tableHeader"
  @addRow="addRow"
  />
  </div>
</template>

<script>
    import MyPopup from '@/components/MyPopup.vue'
    import MySearch from '@/components/MySearch.vue'
    import MyTable from '@/components/MyTable.vue'
    import MyPages from '@/components/MyPages.vue'
  export default {
    components: { MySearch, MyTable, MyPages, MyPopup},
    data(){
      return{
        popup: '',
        showPopup: false,
        tableHeader: [
          {
            headerItem: ['#', 'Название', 'Тип', 'Стоимость']
          }
        ],
        tableData: [
          {
            Items: [
              {
                tableItem: ['1', 'Пюрешка с котлеткой', 'горячее', '200Р'], id: 1 
              },
              
            ]
          },
          {
            Items:[
              {
                tableItem: ['2', 'Оливье', 'Салат', '150Р'], id:2
              },
              {
                tableItem: ['3', 'Чай', 'Напиток', 'бесплатно'], id:3
              }
            ]
          },
        ],
    
        value: '',
        currentPage: 0
      }
    },
    methods:{
    
      setPage(currentPage){
        this.currentPage = currentPage
      },
      
      showPopupToggle(){
        if (this.showPopup == true){
          this.showPopup = false
        }else{
          this.showPopup = true
        }
      },
      addRow(e){
        const input = document.querySelectorAll('.pop-input')
        var x = []
        input.forEach(function(el){
          x.push(el.value)
        })
        this.tableData[this.currentPage].Items.push({tableItem: x})
        localStorage.tableDataMenu = JSON.stringify(this.tableData)
        this.showPopup = false

      },

      removeRow(item){
        this.tableData[this.currentPage].Items = this.tableData[this.currentPage].Items.filter(p => p.id !== item.id)
        localStorage.tableDataMenu = JSON.stringify(this.tableData)

      },


      search(searchValue){
        console.log('hui')
        let tableItems = document.querySelectorAll('.table li')
        var value = searchValue
        if (value != ''){
          tableItems.forEach(function(el){
            if (el.innerText.search(value) == -1){
              el.classList.add('hide')
            }else{
              el.classList.remove('hide');
            }
          });
        } else{
          tableItems.forEach(function(el){
            el.classList.remove('hide')
          })
        }
      }





    },
    mounted(){
      if(localStorage.tableDataMenu){
        this.tableData = JSON.parse(localStorage.tableDataMenu)
      }
    }
  }
</script>

<style scoped>
.table-logo{
  display: flex;
  justify-content: center;
  margin-top: 20px;
}

.end-section{
  display: flex;
  justify-content: space-between;
  width: 100%;
}
.add-button{
  width: 100px;
  display: flex;
  justify-content: center;
  color: #fff;
  align-items: center;
  background: #CB3F3F;
  border-radius: 17px;
  cursor: pointer;
  position: relative;
}
.add-button:hover{
    background: #fff;
    border: 1px solid #CB3F3F;
    color: #000; 
}
</style>