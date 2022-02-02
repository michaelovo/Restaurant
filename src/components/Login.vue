<template>
    <div>
          <img class="logo" alt="Vue logo" src="../assets/logo.png">
        <h1>Login</h1>
    </div>

    <div class="login">
        <!-- <input type="text" v-model="name" placeholder="Enter name"/> -->
        <input type="email" v-model="email" placeholder="Enter email"/>
        <input type="password" v-model="password" placeholder="enter password"/>
        <button :onclick="login">Login</button>
        <p><router-link to="/sign-up">Sign Up</router-link></p>
    </div>
</template>

<script>
import axios from 'axios';
    export default {
        name: 'Login',
        setup(){
            return {
                email: '',
                password: '',
            }
        },
        methods: {
            async login(){
                let result = await axios.get(`http://localhost:3000/user?email=${this.email}&password=${this.password}`);

                 if(result.status == 200 && result.data.length > 0) {
                     // alert("signup done");
                    localStorage.setItem('signUp-info',JSON.stringify(result.data[0]));//store on the browser for easy access
                    this.$router.push({name:'Home'});
                }
                     console.warn(result);
            }
        },
        mounted(){
            //Prevent logged-in user from visiting the login page
            let user = localStorage.getItem('signUp-info');
            if(user){
                this.$router.push({name:'Home'});
            }
        },
    }
</script>

<style scoped>

</style>