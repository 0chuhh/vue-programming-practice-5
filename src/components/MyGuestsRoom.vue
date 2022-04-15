<template>


  <div class="container">
  <div class="kitchen-logo">
    <img src="/assets/GuestsRoom.png"  alt="">
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
  <my-pages
    :currentPage="currentPage"
    :tableData="tableData"
    @setPage="setPage"
  />
  </div>
</template>

<script>
    
    import MySearch from '@/components/MySearch.vue'
    import MyTable from '@/components/MyTable.vue'
    import MyPages from '@/components/MyPages.vue'
  export default {
    components: { MySearch, MyTable, MyPages},
    data(){
      return{
        
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
      
      removeRow(item){
        this.tableData[this.currentPage].Items = this.tableData[this.currentPage].Items.filter(p => p.id !== item.id)
      },


      search(searchValue){
        
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





    }
  }
</script>

<style scoped>

</style>