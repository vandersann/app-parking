<template>
    <nav>
        <router-link  to="/">
        <img :src="logo" alt="alt" id="logo">
        </router-link>
        <router-link to="/">Home</router-link> |
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

<style>

</style>