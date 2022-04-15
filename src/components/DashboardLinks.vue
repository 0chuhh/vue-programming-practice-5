<template>
      <li 
        class = "link"
      >
      <div class="dashboardLogo" >
        <img :src="src" >
      </div>
      <a  href="#"><slot></slot></a></li>
</template>

<script>
    export default {
        props: ['src']
    }
</script>

<style scoped>
a{
  font-family: '';
  color: black;
  text-decoration: none;
  font-size: 24px;
  font-weight: bold;
  line-height: 35px;
  pointer-events: none;
  transition: all 0.3s ease;
}

.link{
  list-style: none;
  display: flex;
  align-items: center;
  padding: 4px 30px 8px 17px;
  cursor: pointer;
}
.link:hover{
  background: #CB3F3F;
  border-radius: 7px;
}
.link:first-child{
  padding-bottom: 20px;
}
.link:last-child{
  padding-bottom: 10px;
  border-bottom-left-radius: 17px;
  border-bottom-right-radius: 17px;
}
img{
  margin-right: 6px;
  width: 19px;
}
.disabled:hover{
  background: #ffff;
}
.disabled a{
  color: #757575;
;
}
.disabled{
  pointer-events: none;
}
</style>