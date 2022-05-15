<template>
<nav class="navbar navbar-light bg-dark">
    <div class="container-fluid">
        <a class="navbar-brand" href="#">
            <div class="logo" ></div>
            <div class="nav-text" >Admin panel</div>
        </a>
    </div>
</nav>
</template>

<script>
    export default {
    }
</script>

<style scoped>

.navbar-brand{
  display: flex;
  align-items: center;

}

.logo{
  content: '';
  width:48px;
  background: #fff;
  height: 48px;
  border-radius: 50%;
  margin-right: 30px;
  margin-left: 40px;
}
.nav-text{
  color: #ffff;
  font-family: 'Istok Web', sans-serif;
  font-style: bold;
  font-size: 24px;
}


</style>