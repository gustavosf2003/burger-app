<template>
  <div id="id">
      <form id="burger-form">
          <div class="main-form">
            <div class="input-container">
                <label for="nome">Nome do cliente</label>
                <input type="text" name="nome" id="nome" v-model="nome" placeholder="Digite seu nome">
            </div>
            <div class="input-container">
                <label for="pao">Escolha o pão:</label>
                <select name="pao" id="pao" v-model="pao">
                    <option value="">Selecione seu pão</option>
                    <option value="integral">integral</option>
                </select>
            </div>
            <div id="opcionais-container" class="input-container">
                    <label for="pao" id="opcionais-title">Selecione os opcionais</label>
                    <div class="checkbox-container">
                        <input type="checkbox" name="opcionais" value="opcionais" v-model="opcionais">
                        <span>Salame</span>
                    </div>
                    <div class="checkbox-container">
                        <input type="checkbox" name="opcionais" value="opcionais" v-model="opcionais">
                        <span>Salame</span>
                    </div>
                    <div class="checkbox-container">
                        <input type="checkbox" name="opcionais" value="opcionais" v-model="opcionais">
                        <span>Salame</span>
                    </div>
            </div>
          </div>
          <div class="input-container">
                <input type="submit" class="submit-btn" value="Criar meu Burger">
          </div>
      </form>
  </div>
</template>

<script>
export default {
    name:"BurgerForm"
}
</script>

<style>
#burger-form{
    max-width: 400px;
    margin: 0 auto;
}
.input-container{
    display: flex;
    flex-direction: column;
    margin-bottom: 20px;
    
}
label{
    font-weight: bold;
    margin-bottom: 15px;
    color: #222;
    padding: 5px 10px;
    border-left: 4px solid #FCBA03;
}
input, select{
    padding: 5px 10px;
    width: 300px;
}
#opcionais-container{
    flex-direction: row;
    flex-wrap: wrap;
}
#opcionais-title{
    width: 100%;
}
.checkbox-container{
    display: flex;
    align-items: flex-start;
    width: 50%;
    margin-bottom: 20px;
}
.checkbox-container span,
.checkbox-container input{
    width: auto;
}
.checkbox-container span{
    margin-left: 6px;
    font-weight: bold;
}
.submit-btn{
    background-color: #222;
    color: #FCBA03;
    font-weight: bold;
    border: 2px solid #222;
    padding: 10px;
    font-size:16px;
    margin: 0 auto;
    cursor: pointer;
    transition: .5s;
    border-radius: 5px;
}
.submit-btn:hover{
    background-color: #353535;
}
</style>