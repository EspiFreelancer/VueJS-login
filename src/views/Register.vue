<template>
    <div class="login">
        <h1 class="title">Login en el sitio</h1>
        <form action class="form" @submit.prevent="register">
            <label for="#email" class="form-label">Email:</label>
            <input 
                v-model="email" 
                type="email" 
                class="form-input" 
                id="email" 
                required 
                placeholder="Email"
            >
            <label for="password" class="form-label">Contraseña</label>
            <input 
                v-model="password"
                type="password"
                class="form-input"
                id="password"
                placeholder="Password"
            >
            <label for="#password-repeat" class="form-label">Repite la contraseña</label>
            <input 
                v-model="passwordRepeat"
                type="password"
                class="form-input"
                id="password-repeat"
                placeholder="Password"
            >            
            <input type="submit" class="form-submit" value="Registrarse">
        </form>
    </div>
</template>

<script>
export default {

  name: 'Register',

  data: () => ({
    email: "",
    password: "",
    passwordRepeat: ""
    }),

  methods: {
    register() {
        console.log(this.email);
        console.log(this.password);
        console.log(this.passwordRepeat);
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
</style>