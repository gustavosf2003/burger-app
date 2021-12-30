<template>
  <div id="main-banner">
      <h1>Make your Burger</h1>
  </div>
</template>

<script>

export default {
    name:"Banner"
}
</script>
<style scoped>
#main-banner{
    background-image: url('/img/burger.jpg');
    background-position: 0 -250px;
    background-size: cover;
    background-repeat: no-repeat;
    height: 500px;
    display: flex;
    align-items: center;
    justify-content: flex-start;
}
@media (max-width: 1000px){
    #main-banner{
        background-position: 0 -150px;
        height: 350px;
    }
}
@media (max-width: 700px){
    #main-banner{
        background-position: 0 -80px;
        height: 250px;
    }
}
@media (max-width: 500px){
    #main-banner{
        background-position: 0 -50px;
        height: 180px;
    }
}
@media (max-width: 1000px){
    #main-banner h1{
        font-size: 2.4rem;
    }
}
@media (max-width: 700px){
    #main-banner h1{
        font-size: 1.5rem;
        color: blue;
    }
}
@media (max-width: 500px){
    #main-banner h1{
        font-size: .9rem;
    }
}
#main-banner h1{
    color: #fff;
    text-align: center;
    background-color: #222;
    padding: 20px 40px;
}
</style>