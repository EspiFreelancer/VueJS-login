<template>
  <div class="home">
    <div v-if="userLogged">
        <p>Usuario: {{ userLogged }}</p>
        <button v-on:click="userLogout">Cerrar sesión</button>
    </div>
    <img alt="Vue logo" src="../assets/logo.png">
    <h2>Gracias por probar Vue-Login con token JWT y Axios</h2>
</div>
</template>

<script>
import auth from "@/logic/auth";

export default {
    name: 'Home',
    computed: {
        userLogged() {
            return auth.getUserLogged();
        }
    },
    methods: {
        userLogout() {
            auth.deleteUserLogged();
            this.$router.push({ name: 'Login' });
        }
    }
};

</script>
