<template>
    <div>
        <router-link to="/login">Login</router-link>
        <router-link to="/register">Register</router-link>
        <h1>Register</h1>
        <form @submit.prevent="handleRegister">
            <div>
                <label for="fname">First Name</label>
                <input type="text" v-model="fname" required />
            </div>
            <div>
                <label for="lname">Last Name</label>
                <input type="text" v-model="lname" required />
            </div>
            <div>
                <label for="email">Email</label>
                <input type="email" v-model="email" required />
            </div>
            <div>
                <label for="password">Password</label>
                <input type="password" v-model="password" required />
            </div>
            <button type="submit">Register</button>
        </form>
    </div>
</template>

<script>
import AuthService from '../services/AuthService';

export default {
    data() {
        return {
            fname: '',
            lname: '',
            email: '',
            password: ''
        };
    },
    methods: {
        async handleRegister() {
            try {
                await AuthService.register({
                    fname: this.fname,
                    lname: this.lname,
                    email: this.email,
                    password: this.password
                });
                this.$router.push('/login');
            } catch (error) {
                alert('Registration failed');
            }
        }
    }
};
</script>
