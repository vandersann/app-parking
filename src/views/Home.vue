<template>
  <main>
    <h1> Cadastrar Veículos </h1>

    <CarForm />
  </main>
</template>

<script>
import CarForm from '@/components/CarForm.vue'

export default {
  name: 'Home',

  components: {
    CarForm,

  }
}
</script>

<style>

</style>