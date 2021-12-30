<template>
  <div>
      <Message :msg="msg" v-if="msg"/>
      <form id="burger-form" @submit="createBurger">
          <div class="main-form">
            <div class="input-container">
                <label for="nome">Nome do cliente</label>
                <input type="text" name="nome" id="nome" v-model="nome" placeholder="Digite seu nome">
            </div>
            <div class="input-container">
                <label for="pao">Escolha o pão:</label>
                <select name="pao" id="pao" v-model="pao">
                    <option disabled>Selecione seu pão</option>
                    <option v-for="pao in paes" :key="pao.id" :value="pao.tipo">{{ pao.tipo }}</option>
                </select>
            </div>
            <div class="input-container">
                <label for="pao">Escolha a carne:</label>
                <select name="pao" id="pao" v-model="carne">
                    <option disabled>Selecione sua carne</option>
                    <option v-for="carne in carnes" :key="carne.id" :value="carne.tipo">{{ carne.tipo }}</option>
                </select>
            </div>
            <div id="opcionais-container" class="input-container">
                    <label for="pao" id="opcionais-title">Selecione os opcionais</label>
                    <div class="checkbox-container" v-for="opcional in opcionaisdata" :key="opcional.id">
                        <input type="checkbox" name="opcionais" :value="opcional.tipo" v-model="opcionais">
                        <span>{{opcional.tipo}}</span>
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
import Message from '../components/Message.vue'
export default {
    name:"BurgerForm",
    components:{
        Message
    },
    data(){
        return{
            paes:null,
            carnes:null,
            opcionaisdata:null,
            nome:null,
            pao:null,
            carne:null,
            opcionais:[],
            msg:null,
        }
    },
    methods:{
        async getIngredients(){
            try{
                const req = await fetch("http://localhost:3000/ingredientes")
                const data = await req.json()
                console.log("Conectado com sucesso")
                this.paes = data.paes;
                this.carnes = data.carnes;
                this.opcionaisdata = data.opcionais;
            }catch(e){
                console.log("Erro ao conecatar ao database :(" + e)
            }
        },
        async createBurger(e){
            //Inserir no banco de dados
            e.preventDefault();
            const data = {
                //juntar os valores para um pedido
                nome: this.nome,
                carne: this.carne,
                pao: this.pao,
                opcionais: Array.from(this.opcionais),
                status: "Solicitado"
            }
            const dataJson = JSON.stringify(data)
            const req = await fetch("http://localhost:3000/burgers",{
                method: "POST",
                headers: { "Content-Type": "application/json" },
                body: dataJson
            })

            const res = await req.json()
            console.log("Cadastrado com sucesso :)")
            
            //mensagem
            this.msg = `Pedido Nº${res.id} realizado com sucesso`

            //limpar msg

            setTimeout(()=> this.msg = "" ,4000)

            //Limpar os campos
            this.nome = "";
            this.carne = "";
            this.pao = "";
            this.opcionais = [];
        }
    },
    mounted(){
        this.getIngredients()
    }
}
</script>

<style>
.main-container{
    margin: 50px;
    min-height: 250px;
}
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