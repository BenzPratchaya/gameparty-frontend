<template>
    <nav class="main-nav">
        <img class="game-logo" alt="Vue logo" src="../assets/game-logo2-Photoroom.png">
        <div class="nav-links">
            <router-link to="/home">Home</router-link>
            <router-link to="/discount">Discount</router-link>
            <router-link to="/category">Category</router-link>
            <router-link to="/threads">Threads</router-link>
            <router-link to="/comment">Comment</router-link>
            <p>Welcome, {{ user?.name }} {{ user?.surname }}</p>
            <button @click="logout">Logout</button>
        </div>
    </nav>
</template>

<script>
import AuthService from '../services/AuthService';

export default {
    name: 'NavbarView',
    data() {
        return {
            user: null
        };
    },
    created() {
        this.user = JSON.parse(localStorage.getItem('user'));
    },
    methods: {
        logout() {
            AuthService.logout();
            this.$router.push('/login');
        }
    }
};
</script>

<style>
.main-nav {
    display: flex;
    align-items: center;
    justify-content: space-between;
    background-color: #2c3e50;
    padding: 20px;
    border-radius: 8px;
    box-shadow: 0 4px 6px rgba(0, 0, 0, 0.1);
    margin-bottom: 40px;
}

.game-logo {
    width: 10%;
    max-width: 100px;
    height: auto;
}

.nav-links {
    display: flex;
    gap: 20px;
    align-items: center; /* Adjust alignment */
}

.nav-links a {
    text-decoration: none;
    color: #ffffff;
    padding: 10px 15px;
    border-radius: 5px;
    transition: background-color 0.3s;
}

.nav-links p {
    margin: 0; /* Remove default margin */
    color: #ffffff;
    font-weight: bold; /* Make the text bold */
}

.nav-links button {
    padding: 8px 15px; /* Adjust button padding */
    border: none;
    border-radius: 5px;
    background-color: #e74c3c; /* Red background color */
    color: white;
    cursor: pointer;
    transition: background-color 0.3s;
}

.nav-links button:hover {
    background-color: #c0392b; /* Darker red on hover */
}

.nav-links a:hover {
    background-color: #1abc9c;
}

.nav-links a.router-link-exact-active {
    background-color: #16a085;
    font-weight: bold;
}
</style>
