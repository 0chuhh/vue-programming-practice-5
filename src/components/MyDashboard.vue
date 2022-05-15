<template>
    <div class="dashboard" :style="{background: `${darkMode? '#000': '#fff'}`}">
    <ul>
        <slot></slot>
    </ul>
    </div>
</template>

<script>
    export default {
        props:['darkMode']
    }
</script>

<style>
.dashboard{
  position: fixed;
  top: 35vh;
  z-index: 10;
  background: #ffff;
  margin-left: 30px;
  width: 270px;
  border-radius: 17px;
  box-shadow: 0px 4px 16px rgba(0, 0, 0, 0.25);
  max-height: 408px;
  transition: all 0.3s ease;
    box-sizing: unset;

}
ul{
    margin: 0;
    padding: 20px 0 0 0;
}
.minimized a{
    font-size: 0;
}
.minimized .link{
    padding: 4px 0 8px 17px;
}
.minimized{
    width: 55px;
}
</style>