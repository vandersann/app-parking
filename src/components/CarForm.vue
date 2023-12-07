<template>
    <div>

        <Mensagem  :msg="msg" v-show="msg" />

        <form id="carro-form" @submit="createCarro">
            <div class="input-container">
                <label for="nome">Nome do Cliente </label>
                <input type="text" id="nome" v-model="nome" placeholder="Seu nome">
            </div>
            <div class="input-container">
                <label for="fabricante">Fabricante </label>
                <input type="text" id="fabricante" v-model="fabricante" placeholder="Fabricante do veículo">
            </div>
            <div class="input-container">
                <label for="modelo">Modelo do Carro </label>
                <input type="text" id="modelo" v-model="modelo" placeholder="Modelo do veículo">
            </div>
            <div class="input-container">
                <label for="cor">Cor do Carro </label>
                <input type="text" id="cor" v-model="cor" placeholder="Cor do veículo">
            </div>
            <div class="input-container">
                <label for="ano">Ano de Fabricação </label>
                <input type="text" id="ano" v-model="ano" placeholder="Ano de fabricação">
            </div>
            <div class="input-container">
                <label for="placa">Placa do Carro </label>
                <input type="text" id="placa" v-model="placa" placeholder="Placa do veículo">
            </div>
            <div class="input-container">
                <label for="hora">Hórario de Entrada </label>
                <input type="time" id="hora" v-model="hora" placeholder="Informe o hórario de entrada">
            </div>
            <div class="input-container btn">
                <button class="submit-btn" value="Cadastrar">Cadastrar</button>

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
                fabricante: null,
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
                    fabricante: this.fabricante,
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
                this.fabricante = "";
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
        max-width: 420px;
        margin: 0 auto;
    }

    .input-container {
        display: flex;
        flex-direction: row;
        margin-bottom: 1.5rem;
        align-items: center;
        justify-content: space-between;
        box-shadow: rgba(99, 99, 99, 0.2) 0px 2px 8px 0px;
    }

    label {
        font-weight: bold;
        margin-bottom: 10px;
        color: black;
        padding: 5px 10px;
    }

    input {
        padding: 8px 20px;
        widows: 300px;
        font-size: 1rem;
    }

    .input-container.btn {
        display: flex;
        align-items: center;
        justify-content: center;
        box-shadow: none;
        text-transform: capitalize;
    }

    .input-container.btn .submit-btn {
        color: #1E88E5;
        font-size: 1.2rem;
        background-color: #fff;
        cursor: pointer;
        position: relative;
        width: 50%;
        height: 2.4rem;
        border: 2px solid #1E88E5;
        border-radius: .4rem;
        box-shadow: rgba(0, 0, 0, 0.15) 1.95px 1.95px 2.6px;
        transition: all 0.4s cubic-bezier(0.42, 0, 0.58, 1);
    }
    .input-container .submit-btn:hover {
        color: #fff !important;
        background-color: transparent;
        text-shadow: nthree;
    }
    .input-container .submit-btn:hover::before {
        left: 0%;
        right: auto;
        width: 100%;
    }
    .input-container .submit-btn::before {
        display: block;
        position: absolute;
        top: 0px;
        right: 0px;
        height: 100%;
        width: 0px;
        z-index: -1;
        content: '';
        color: #000 !important;
        background: #1E88E5;
        transition: all 0.4s cubic-bezier(0.42, 0, 0.58, 1);
    }

    .delete-btn i{
        margin-left: .2rem;
        font-size: 1.2rem;
    }

</style>