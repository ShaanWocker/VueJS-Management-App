<template>
    <img class="logo" src="../assets/yinjang.png"/>
    <h1>Sign Up</h1>
    <div class="register">
        <input type="text" placeholder="Name"/>
        <input type="text" placeholder="Email"/>
        <input type="password" placeholder="Password"/>
        <button>Sign Up</button>
    </div>
</template>

<script>
    export default {
        name:'SignUp'
    }
</script>

<style>
.logo{
  width: 100px;
}
.register input{
    width: 300px;
    height: 40px;
    padding-left: 20px;
    display: block;
    margin-bottom: 30px;
    margin-right: auto;
    margin-left: auto;
    border: 1px solid black;
}
.register button{
    width: 320px;
    height: 40px;
    border: 1px solid black;
    background: black;
    color: #ffffff;
    cursor: pointer;
}
</style>