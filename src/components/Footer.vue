<template>
  <div id="footer">
    <p>Make Your Burger &copy; {{year}}</p>
  </div>
</template>

<script>
export default {
  name: "Footer",
  data(){
    return{
      year: new Date().getFullYear()
    }
  }
}
</script>

<style scoped>
#footer{
  height: 200px;
  background-color: #222;
  color: #FCBA03;
  display: flex;
  align-items: center;
  justify-content: center;
  width: 100%;
}
</style>