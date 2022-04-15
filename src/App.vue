<template>

  

  <my-nav/>
  
  <sign-up
    :canEnter="canEnter"
    @checkPas="signup"
    :class="correctLoginPass == false ? 'noncorrect': ''"
  />
  <my-dashboard
    v-if="canEnter"
    @mouseenter="hover = true"
    @mouseleave="hover = false"
    :class="hover == true ? '': 'minimized'"  
  >
  <dashboard-links
    @click="selected"
    v-for="(text, index) in dashboard[0].links"
    :key="index"
    :id="index"
    :src="dashboard[0].Dlogos[index]"
    :class="index == 0? 'disabled': ''"
  > {{dashboard[0].links[index]}} </dashboard-links>
  </my-dashboard>

  <mykitchen
    v-if="CurrentSection == 1"
  />
  <my-guests-room
    v-if="CurrentSection == 2"
  />
</template>

<script>
import SignUp from '@/components/SignUp.vue'
import MyNav from '@/components/MyNav.vue'
import DashboardLinks from '@/components/DashboardLinks.vue'
import MyDashboard from '@/components/MyDashboard.vue'
import Mykitchen from '@/components/Mykitchen.vue'
import MyGuestsRoom from '@/components/MyGuestsRoom.vue'
  export default {
    components: {SignUp,MyNav,MyDashboard, DashboardLinks, Mykitchen, MyGuestsRoom},
    data(){
      return{
        dashboard: [
          {links: ['Dashboard', 'Кухня', 'Зал', 'Меню', 'Склад', 'Финансы', 'Реклама', 'Настройка'], Dlogos: ['./assets/Home-icon.png', './../assets/chef.png', './../assets/food-serving.png', './assets/menu.png', './assets/sklad.png', './assets/income.png', './assets/megaphone.png','./assets/preference.png']}
        ],
        
        CurrentSection:false,
          
        canEnter: false,
        correctLoginPass: true,
        hover: false,
        isActive: false,
        value: '',
        currentPage: 0
      }
    },
    methods:{
      selected(e){
        this.CurrentSection = e.target.id
      },

      signup(login, pass){
        if (login == 'admin' && pass == 'admin'){
          this.canEnter = true
        }else{
          alert('Не верный логин или пароль!')
          this.correctLoginPass = false
        }
      }




    }
  }
</script>
<style>
body{
  font-family: 'Istok Web', sans-serif;
  background: #EFEFEF;
}

.kitchen-logo{
  display: flex;
  justify-content: center;
  margin-top: 20px;
}

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
.container{
  max-width: 1288px;
  padding: 0;
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
.signup{
  background: #FFFFFF;
  box-shadow: 0px 4px 10px rgba(0, 0, 0, 0.25);
  width: 340px;
  height: 408px;
  border-radius: 17px;
  display: flex;
  justify-content: center;
  align-items: center;
  flex-direction: column;
  margin: 0 auto;
  margin-top: 10%;
}
 .login,.password{
  width: 300px;
  margin-left: 20px;
}
.signup p{
  padding: 0;
  margin: 5px 0;
}
.btn{
  margin-top: 20px;
  background: #CB3F3F;
  color: #fff;
}
.btn:hover{
  background: #fff;
  border: 1px solid #CB3F3F;
}
.noncorrect input{
  border: 1px solid red
}
.noncorrect input:focus{
  outline: none;
}

</style>