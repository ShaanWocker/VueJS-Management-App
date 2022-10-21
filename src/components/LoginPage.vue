<template>
    <img class="logo" src="../assets/yinjang.png"/>
    <h1>Login Page</h1>
    <div class="login">
        <input type="text" v-model="email" placeholder="Email"/>
        <input type="password" v-model="password" placeholder="Password"/>
        <button v-on:click="login">Login</button>
        <p>
            <router-link to="/sign-up">Sign Up</router-link>
        </p>
    </div>
</template>
<script>
    export default {
        name:'LoginPage'
    }
</script>
<style>
.logo{
  width: 100px;
}
.login input{
    width: 300px;
    height: 40px;
    padding-left: 20px;
    display: block;
    margin-bottom: 30px;
    margin-right: auto;
    margin-left: auto;
    border: 1px solid black;
}
.login button{
    width: 320px;
    height: 40px;
    border: 1px solid black;
    background: black;
    color: #ffffff;
    cursor: pointer;
}
</style>