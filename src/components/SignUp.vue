<template>
    <div v-if="canEnter == false" class="signup">
            <h1>LOGIN</h1>
        
        <div class="login">
            <p>login</p>
            <input  @keyup.enter="$emit('checkPas', login, password)" v-model="login" type="text">
        </div>
        <div class="password">
            <p>password</p>
            <input  @keyup.enter="$emit('checkPas', login, password)" v-model="password" type="text">
        </div>
        <button @click="$emit('checkPas', login, password)" class="btn">Войти</button>
    </div>
</template>

<script>
    export default {
        data(){
            return{
                login: 'admin',
                password: 'admin'
            }
        },
        
        props: ['canEnter'],
        methods:{
            
        }
    }
</script>

<style scoped>

</style>