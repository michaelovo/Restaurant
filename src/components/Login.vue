<template>
    <div>
          <img class="logo" alt="Vue logo" src="../assets/logo.png">
        <h1>Login</h1>
    </div>

    <div class="login">
        <!-- <input type="text" v-model="name" placeholder="Enter name"/> -->
        <input type="email" v-model="email" placeholder="Enter email"/>
        <input type="password" v-model="password" placeholder="enter password"/>
        <button>Login</button>
        <p><router-link to="/sign-up">Sign Up</router-link></p>
    </div>
</template>

<script>
    export default {
        name: 'Login',
    }
</script>

<style scoped>

</style>