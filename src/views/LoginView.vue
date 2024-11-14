<template>
    <div>
        <router-link to="/login">Login</router-link>
        <router-link to="/register">Register</router-link>
        <h1>Login</h1>
        <form @submit.prevent="handleLogin">
            <div>
                <label for="email">Email</label>
                <input type="email" v-model="email" required />
            </div>
            <div>
                <label for="password">Password</label>
                <input type="password" v-model="password" required />
            </div>
            <button type="submit">Login</button>
        </form>
    </div>
</template>

<script>
import AuthService from '../services/AuthService';

export default {
    data() {
        return {
            email: '',
            password: ''
        };
    },
    methods: {
        async handleLogin() {
            try {
                await AuthService.login({ email: this.email, password: this.password });
                this.$router.push('/home');
            } catch (error) {
                alert('Invalid credentials');
            }
        }
    }
};
</script>
