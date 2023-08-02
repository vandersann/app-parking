<template>
    <div>
        <div id="carro-form">
            <div class="input-container">
                <label for="nome">Nome do Cliente: </label>
                <input type="text" id="nome" v-model="nome" placeholder="Insira seu nome">
            </div>
            <div class="input-container">
                <label for="modelo">Modelo do Carro: </label>
                <input type="text" id="modelo" v-model="modelo" placeholder="Insira o modelo do veículo">
            </div>
            <div class="input-container">
                <label for="cor">Cor do Carro: </label>
                <input type="text" id="cor" v-model="cor" placeholder="Insira a cor do veículo">
            </div>
            <div class="input-container">
                <label for="ano">Ano de Fabricação: </label>
                <input type="text" id="ano" v-model="ano" placeholder="Insira o ano de fabricação">
            </div>
            <div class="input-container">
                <label for="placa">Placa do Carro: </label>
                <input type="text" id="placa" v-model="placa" placeholder="Insira a placa do veículo">
            </div>
            <div class="input-container">
                <label for="hora">Hórario de Entrada </label>
                <input type="time" id="hora" v-model="hora" placeholder="Informe o hórario de entrada">
            </div>
            <div class="input-container">
                <input type="submit" class="submit-btn" value="Cadastrar">
            </div>
        </div>
    </div>
</template>

<script>
export default {
    name: "CarForm"
}

</script>

<style scoped>

    #carro-form {
        max-width: 300px;
        margin: 0 auto;
    }

    .input-container {
        display: flex;
        flex-direction: column;
        margin-bottom: 25px;
    }

    label {
        font-weight: bold;
        margin-bottom: 15px;
        color: black;
        padding: 5px 10px;
        border-left: 4px solid #3f7fbf;
    }

    input {
        padding: 5px 10px;
        widows: 300px;
    }

    .submit-btn {
        background-color: #3f7fbf;
        color: white;
        font-weight:bold;
        padding: 10px;
        font-size: 16px;
        border: 2px solid white;
        cursor: pointer;
        transition: .5s;
    }

    .submit-btn:hover{
        background-color:black;
        font-size: 18px;
    }

</style>