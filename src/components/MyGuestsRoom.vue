<template>


  <div class="container">
  
  <div class="table-logo">
    <img src="/assets/GuestsRoom.png" alt="">
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
            headerItem: ['#', 'Фамилия', 'Имя', 'Отчество', 'Должность', 'Зарплата', 'Рабочие часы']
          }
        ],
        tableData: [
          {
            Items: [
              {
                tableItem: ['1', 'Петров', 'Петр', 'Петрович', 'Шеф-повар', '1000000', '6:30-18:00'], id: 1 
              },
              {
                tableItem: ['2', 'Иванов', 'Иван', 'Петрович', 'Су-шеф', '10000', '6:30-18:00'], id:2
              },
              {
                tableItem: ['3', 'Данилова', 'Виктория', 'Данииловна','Повар', '10000', '6:30-18:00'], id:3
              },
              {
                tableItem: ['4', 'Маркелов', 'Роман', 'Кириллович', 'Повар', '10000', '6:30-18:00'], id:4
              },
              {
                tableItem: ['5', 'Иванов', 'Богдан', 'Тимофеевич', 'Повар', '10000', '6:30-18:00'], id:5
              },
              {
                tableItem: ['6', 'Мухина', 'Вероника', 'Максимовна', 'Повар', '10000', '6:30-18:00'], id:6
              },
              {
                tableItem: ['7', 'Блинов', 'Константин', 'Вячеславович', 'Повар', '10000', '6:30-18:00'], id:7
              },

            ]
          },
          {
            Items:[
              {
                tableItem: ['8', 'Петров', 'Петр', 'Петрович', 'Директор', '1000000', '6:30-18:00'], id:8
              },
              {
                tableItem: ['9', 'Иванов', 'Иван', 'Петрович', 'Менеджер', '10000', '6:30-18:00'], id:9
              }
            ]
          },
          {
            Items:[
              {
                tableItem: ['10', 'Петров', 'Петр', 'Петрович', 'Директор', '1000000', '6:30-18:00'], id:10
              },
              {
                tableItem: ['11', 'Иванов', 'Иван', 'Петрович', 'Менеджер', '10000', '6:30-18:00'], id:11
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
        localStorage.tableDataGuests = JSON.stringify(this.tableData)
        this.showPopup = false

      },

      removeRow(item){
        this.tableData[this.currentPage].Items = this.tableData[this.currentPage].Items.filter(p => p.id !== item.id)
        localStorage.tableDataGuests = JSON.stringify(this.tableData)

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
      if(localStorage.tableDataKitchen){
        this.tableData = JSON.parse(localStorage.tableDataGuests)
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