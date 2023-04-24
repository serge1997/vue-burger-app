<template>
    
    <div class="burger-form">
        <form id="form-burg">
            <div class="input-container">
                <label for="nome">Nome do cliente: </label>
                <input type="text" v-model="nome" placeholder="Digite o seu nome">
            </div>
            <div class="input-container">
                <label for="pao">Escolhe o pão: </label>
                <select name="pao" v-model="pao" id="pao">
                    <option value="">Escolhe seu pão</option>
                    <option value="Integral">Integral</option>
                </select>
            </div>
            <div class="input-container">
                <label for="carne">Escolhe a carne do seu Burger: </label>
                <select name="carne" v-model="carne" id="carne">
                    <option value="">Escolhe o tipo de carne</option>
                    <option value="Integral">Integral</option>
                </select>
            </div>
            <div id="checkbox-container">
                <label for="carne">Selecione os opcionais:  </label>
                <div id="input-checkbox">
                    <div>
                        <input type="checkbox" name="opcionais" v-model="opcionais" value="salame">
                        <span>Salame</span>
                    </div>
                    <div>
                        <input type="checkbox" name="opcionais" v-model="opcionais" value="salame">
                        <span>Salame</span>
                    </div>
                    <div>
                        <input type="checkbox" name="opcionais" v-model="opcionais" value="salame">
                        <span>Salame</span>
                    </div>
                    <div>
                        <input type="checkbox" name="opcionais" v-model="opcionais" value="salame">
                        <span>Salame</span>
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

    export default {
        name: 'BurgerForm'
    }

</script>

<style scoped>
    .burger-form {
        padding: 18px;
        margin: 22px;
        display: flex;
        justify-content: center;
        justify-items: center;
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
        display: flex;
        flex-direction: column;
        justify-content: flex-start;
        margin: 8px 0px 8px 0px;
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
        width: 87%;
        display: flex;
        gap: 6px;
        flex-wrap: wrap;
    }

    #submit-container .btn-submit {
        background-color: #222;
        color: #fff;
        border: none;
        padding: 8px 0px 8px 0px;
    }
    
    
</style>