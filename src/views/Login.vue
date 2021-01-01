<template>
    <div class="login">
        <h1 class="title">Login en el sitio</h1>
        <form action class="form" @submit.prevent="login">
            <label for="#email" class="form-label">Email:</label>
            <input 
                v-model="email"
                type="email"
                class="form-input"
                id="email"
                required
                placeholder="Email"
            >
            <label for="#password" class="form-label">Contraseña</label>
            <input 
                v-model="password"
                type="password"
                class="form-input"
                id="password"
                placeholder="Password"
            >
            <p v-if="error" class="error">Has introducido mal el email o la contraseña.</p>
            <input type="submit" class="form-submit" value="Login">
        </form>
        <p class="msg">¿No tienes una cuenta?
            <router-link to="{ name: 'Register' }">Regístrate</router-link></p>
    </div>
</template>

<script>
import auth from "@/logic/auth";
export default {

  name: 'Login',

  data: () => ({
    email: "",
    password: "",
    error: false
    }),

  methods: {
    async login() {
        try {
            await auth.login(this.email, this.password);
            this.$router.push({ name: 'Home' });
        } catch (error) {
            this.error = true;
        }
    }

  }
};
</script>

<style lang="scss" scoped>
.login {
    padding: 2rem;
}
.title {
    text-align: center;
}
.form {
    margin: 3rem auto;
    display: flex;
    flex-direction: column;
    justify-content: center;
    width: 20%;
    min-width: 350px;
    max-width: 100%;
    background: rgb(19, 35, 47, 0.9);
    border-radius: 5px;
    padding: 40px;
    box-shadow: 0 4px 10px 4px rgba(0, 0, 0.3);
}
.form-label {
    margin-top: 2rem;
    color: white;
    margin-bottom: 0,5rem;
    &:first-of-type {
        margin-top: 0rem;
    }
}
.form-input {
    padding: 10px 15px;
    background: none;
    background-image: none;
    border: 1px solid white;
    color: white;
    &:focus {
        outline: 0;
        border-color: #1ab188;
    }
}
.form-submit {
    font-size: 1.3rem;
    background: #1ab188;
    borfer: none;
    color: white;
    margin-top: 3rem;
    padding: 1rem 0;
    cursor: pointer;
    transition: background 0.2s;
    &:hover {
        background: #0b9185;
    }
}
.error {
    margin: 1rem 0;
    color: #ff4a96;
}
</style>