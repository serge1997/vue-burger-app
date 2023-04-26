<template>
    
    <div class="burger-form">
        
    
        
        <form id="form-burg" @submit="createBurger">
            <Message :msg="msg" v-show="msg" />
            <div class="input-container">
                <label for="nome">Nome do cliente: </label>
                <input class="border border-slate-400" type="text" v-model="nome" placeholder="Digite o seu nome">
            </div>
            <div class="input-container">
                <label for="pao">Escolhe o pão: </label>
                <select class="border border-slate-400" name="pao" v-model="pao" id="pao">
                    <option value="">Escolhe seu pão</option>
                    <option v-for="pao in paes" :key="pao.id" :value="pao.tipo"> {{ pao.tipo }}</option>
                </select>
            </div>
            <div class="input-container">
                <label for="carne">Escolhe a carne do seu Burger: </label>
                <select class="border border-slate-400" name="carne" v-model="carne" id="carne">
                    <option value="">Escolhe o tipo de carne</option>
                    <option v-for="carne in carnes" :key="carne.id" :value="carne.tipo"> {{ carne.tipo }} </option>
                </select>
            </div>
            <div id="checkbox-container">
                <label for="carne">Selecione os opcionais:  </label>
                <div id="input-checkbox">
                    <div v-for="opcao in opcionaisdata" :key="opcao.id">
                        <input type="checkbox" name="opcionais" v-model="opcionais" :value="opcao.tipo">
                        <span> {{ opcao.tipo }} </span>
                    </div>
                </div>
            </div>
            <div id="submit-container">
                <input type="submit" value="Criar meu Burger" class="btn-submit">
            </div>
        </form>
    </div>
</template>

<script>
import Message from './Message.vue'
    
    export default {
        name: 'BurgerForm',

        components: {
            Message
        },

        data() {
            return {
                paes: null,
                carnes: null,
                opcionaisdata: null,
                nome: null,
                pao: null,
                carne: null,
                opcionais: [],
                msg: null 
            }
        },

        methods: {
            async getIngredientes() {

                const req = await fetch('http://localhost:3000/ingredientes')
                const data = await req.json()

                this.paes = data.paes;
                this.carnes = data.carnes;
                this.opcionaisdata = data.opcionais
            
            },

            async createBurger(e) {

                e.preventDefault()

                const data = {
                    nome: this.nome,
                    carne: this.carne,
                    pao: this.pao,
                    opicionais: Array.from(this.opcionais), //objeto checkboc em array
                    status: "Solicitado"
                }

                const dataJson = JSON.stringify(data);

                const req = await fetch('http://localhost:3000/burgers', {
                    method: 'POST',
                    headers: { 'Content-Type': 'application/json'},
                    body: dataJson
                });

                const res = await req.json();

                console.log(res)

                this.msg = `Pedido N ${res.id} realizado com sucesso !!`;

                setTimeout(() => this.msg = "", 3000);

                //deixando os campos vazios depois de submit

                this.nome = "";
                this.carne = "";
                this.pao = "";
                this.opcionais = "";

            }

        },

        mounted() {
           this.getIngredientes()

        }
    }

</script>

<style scoped>
    .burger-form {
        width: 100%;
        padding: 18px;
        margin: 22px;
        display: flex;
        justify-content: center;
        justify-items: center;
    }

    form {
        display: flex;
        flex-direction: column;
        justify-content: center;
        align-items: center;
    }

    .input-container {
        display: flex;
        flex-direction: column;
        gap: 9px;
    }

    label{
        font-weight: bold;
        color: #222;
        margin-top: 8px;
        padding: 4px 5px;
        border-left: solid 6px #fcba03;
    }

    input, select {
        padding: 5px 10px;
        width: 300px;
    }

    #checkbox-container {
        margin: auto;
        display: flex;
        flex-direction: column;
        justify-content: center;
        align-items: center;
        margin: 8px 0px 8px 0px;
    }

    #checkbox-container label {
        margin-left: -105px;
    }
    #checkbox-container input{
        width: 26px;
        margin: 16px 0px 8px 0px;
        border: solid 6px #222;
    }

    #checkbox-container span{
        font-weight: bold;
    }

    #input-checkbox {
        width: 60%;
        display: flex;
        gap: 6px;
        flex-wrap: wrap;
    }

    

    #submit-container .btn-submit {
        background-color: #222;
        color: #fff;
        border: none;
        padding: 8px 0px 8px 0px;
        cursor: pointer;
        transition: .5s;
    }

    #submit-container .btn-submit:hover{
        background: #fcba03;
        color: #222;
    }

    #msg {
        text-align: center;
        color: #222;
        font-weight: 700;
        margin-bottom: 12px;
        padding: 6px;
    }

    
    
</style>