<template>
    <div>
          <img class="logo" alt="Vue logo" src="../assets/logo.png">
        <h1>Signup form</h1>
    </div>

    <div class="register">
        <input type="text" value="" placeholder="Enter name"/>
        <input type="text" value="" placeholder="Enter email"/>
        <input type="text" value="" placeholder="enter password"/>
        <button>Login</button>
    </div>
</template>

<script>
export default {
    name: 'Signup',
    setup () {
        return {}
    }
}
</script>

<style>
.logo {
    width: 100px;
}
.register input {
    width: 300px;
    height: 40px;
    padding-left: 20px;
    display: block;
    margin-bottom: 30px;
    margin-right : auto;
    margin-left: auto;
    border: 1px solid skyblue;
}
.register button {
    width: 320px;
    height: 40px;
    border: 1px solid skyblue;
    background-color:skyblue;
    color: white;
    cursor: pointer;
}

</style>