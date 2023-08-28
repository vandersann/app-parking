<template>
    <div>

        <Mensagem  :msg="msg" v-show="msg" />

        <form id="carro-form" @submit="createCarro">
            <div class="input-container">
                <label for="nome">Nome do Cliente: </label>
                <input type="text" id="nome" v-model="nome" placeholder="Insira seu nome">
            </div>
            <div class="input-container">
                <label for="marca">Marca do Carro: </label>
                <input type="text" id="marca" v-model="marca" placeholder="Insira a marca do veículo">
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
        </form>
    </div>
</template>

<script>

    import Mensagem from './Mensagem'

    export default {
        name: "CarForm",

        components: {
            Mensagem,
        },

        data() {
            return {
                nome: null,
                marca: null,
                modelo: null,
                cor: null,
                ano: null,
                placa: null,
                hora: null,
                msg: null,
                status: null,
            }
        },
        methods: {
            async createCarro(e){
                e.preventDefault();

                const data = {
                    nome: this.nome,
                    marca: this.marca,
                    modelo: this.modelo,
                    cor: this.cor,
                    ano: this.ano,
                    placa: this.placa,
                    hora: this.hora,
                    status: "Solicitado"
                }

                const dataJson = JSON.stringify(data);

                const req = await fetch("http://localhost:3000/carros", {
                    method: "POST",
                    headers: {"Content-Type" : "application/json"},
                    body: dataJson
                });

                const res = await req.json();

                console.log(res);

            //  Mensagem de confirmação de cadastro
            this.msg = ` Carro Cadastrado com sucesso! `;

            // Limpar a Mensagem após tempo sugerido
            setTimeout(()=> this.msg = "", 3000)

                // Limpar campos
                this.nome = "";
                this.marca = "";
                this.modelo = "";
                this.cor = "";
                this.ano = "";
                this.placa = "";
                this.hora = "";
            }
        }
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
        margin-bottom: 10px;
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