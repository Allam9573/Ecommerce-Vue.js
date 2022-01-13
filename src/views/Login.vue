<template>
<BasicLayout>
    <div class="container">
        <h2>Inicio de Sesion:</h2>
        <router-link to="/register">Crear una cuenta</router-link>
    </div>
</BasicLayout>
</template>

<script>
import BasicLayout from '../layout/BasicLayout.vue'
export default {
  name: "Login",
  components:{
      BasicLayout
  }
};
</script>

<style>
</style>