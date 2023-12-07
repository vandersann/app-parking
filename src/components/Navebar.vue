<template>
    <nav>
        <figure class="gif" >
            <img src="/public/img/car.gif">
        </figure>
        <router-link  to="/" id="logo-url">

            <img :src="logo" :alt="alt" id="logo">
        </router-link>
        <router-link to="/">Home</router-link>
        <router-link to="/cadastro">Cadastro</router-link>
    </nav>
</template>

<script>
    export default {
        name: "Navebar",
        props: [
            "logo",
            "alt",
        ]
    }
</script>

<style scoped>

    .gif{
        text-align: center;
        padding: 15px;
        background-color: black;
        width: 10rem;
    }

    nav{
        background-color: #1E88E5;
        padding: 15px 50px;
        display: flex;
        justify-content: flex-end;
        align-items: center;
    }

    nav #logo-url{
        margin: auto;
        margin-left: 0;
    }

    #logo{
        width: 40px;
        height: 40px;
    }

    nav a{
        color: #FFF;
        padding: .2rem;
        text-decoration: none;
        margin: 12px;
        transition: .5s;
        font-size: 1.4rem;
    }

    nav a:hover{
        opacity: 1;
        box-shadow: rgb(38, 57, 77) 0px 20px 30px -10px;
    }

</style>