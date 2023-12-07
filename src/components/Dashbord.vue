<template>


    <div id="table-car">

        <Mensagem :msg="msg" v-show="msg" />

    <div>


        <div id="table-car-heading">

                <div class="order-id"># </div>
                <div>Nome do Cliente </div>
                <div>Fabricante</div>
                <div>Modelo</div>
                <div>Cor</div>
                <div>Ano</div>
                <div>Placa</div>
                <div>Hora da Entrada </div>
                <div>Ações </div>

        </div>

    </div>


        <div id="table-car-rows">

            <div class="table-car-row" v-for="carro in carros" :key="carro.id" >

                <div class="order-number">{{ carro.id }}</div>
                <div>{{ carro.nome }} </div>
                <div>{{ carro.fabricante }}</div>
                <div>{{ carro.modelo }}</div>
                <div>{{ carro.cor }}</div>
                <div>{{ carro.ano }}</div>
                <div>{{ carro.placa }}</div>
                <div>{{ carro.hora }}</div>

            <div>

                <select name="status" class="status"  @change="updateCarro($event, carro.id)">
                    <option value="statu.id">Status Carro </option>
                    <option :value="statu.tipo" v-for="statu in status" :key="statu.id" :selected="carro.status == statu.tipo"> {{ statu.tipo }} </option>
                </select>

                <button class="delete-btn" @click="deletarCarro(carro.id)"> Deletar <i class='bx bx-x-circle'></i></button>

            </div>

        </div>

    </div>

</div>


</template>

<script>

    import Mensagem from './Mensagem.vue';

    export default {
        name: "Dashboard",

        data() {
            return {
                carros: null,
                carros_id: null,
                status: [],
                msg : null
            }
        },

        // component mensagem

        components : {

            Mensagem,
        },

        // Carregar os Carros

        methods: {

            async getCadastros() {

                const req = await fetch("http://localhost:3000/carros");

                const data = await req.json();

                this.carros = data;

                this.getStatus();

            },

            async getStatus() {

                const req = await fetch("http://localhost:3000/status");

                const data = await req.json();

                this.status = data;
            },

            async deletarCarro(id) {

                const req  = await fetch(`http://localhost:3000/carros/${id}`, {
                    method: "DELETE"

                });

                const data = await req.json();


                 //  Mensagem de cadastro de carro
               this.msg = `Carro DELETADO com sucesso!`;

                // Limpar a Mensagem após um tempo
                setTimeout(() => this.msg = "", 3000)

                this.getCadastros();


            },

            // Atualizando o status do CARRO

            async updateCarro(event, id){

                const opcoes = event.target.value;

                const dataJson = JSON.stringify({ status: opcoes }); // pega o ID do STATUS e CARROS

                const req =  await fetch(`http://localhost:3000/carros/${id}`, {
                    method: "PATCH", // atualiza somente o ID do STATUS
                    headers: { "Content-Type" : "application/json" },
                    body: dataJson
                });

                const res = await req.json();


                 //  Mensagem de cadastro de carro
               this.msg = `Veículo de placa ${res.placa} foi atualizado para ${res.status}.`;

                // Limpar a Mensagem após um tempo
                setTimeout(() => this.msg = "", 3000)


                console.log(res);



            }

        },

        mounted() {

            this.getCadastros();
        }


    }


</script>


<style scoped>


    #table-car {

        max-width: 90%;
        margin: 0 auto;

    }

    #table-car-heading,
    #table-car-rows
    .table-car-row {
        display: flex;
        flex-wrap: wrap;
        align-items: center;
        justify-content: space-between;
        font-size: 1.2rem;
    }

    #table-car-heading{
        font-weight: bold;
        padding: 1.2rem;
        border-bottom: 0.3rem solid rgba(53,30,180);
    }

    #table-car-heading div,
    .table-car-row div {
        width: 10%;
    }

    .table-car-row {
        width: 100%;
        padding: 1.2rem;
        border-bottom: 1px solid rgba(53,30,180);

    }

    #table-car-heading .order-id,
    .table-car-row .order-number {
        width: 5%;
    }

    .status {
        height: 2rem;
        margin-bottom: .4rem;
        box-shadow: rgba(99, 99, 99, 0.2) 0px 2px 8px 0px;
    }

    .status select {
        padding:  .8rem .6rem;
        margin-right: 1rem;
        width: 50%;
    }

    .delete-btn {
        color: #AE354C;
        background-color: #fff;
        cursor: pointer;
        display: block;
        position: relative;
        width: 75%;
        height: 2rem;
        border: 2px solid #AE354C;
        box-shadow: rgba(99, 99, 99, 0.2) 0px 2px 8px 0px;
        transition: all 0.4s cubic-bezier(0.42, 0, 0.58, 1);
    }
    .delete-btn:hover {
        color: #fff !important;
        background-color: transparent;
        text-shadow: nthree;
    }
    .delete-btn:hover:before {
        left: 0%;
        right: auto;
        width: 100%;
    }
    .delete-btn:before {
        display: block;
        position: absolute;
        top: 0px;
        right: 0px;
        height: 100%;
        width: 0px;
        z-index: -1;
        content: '';
        color: #000 !important;
        background: #AE354C;
        transition: all 0.4s cubic-bezier(0.42, 0, 0.58, 1);
    }

</style>