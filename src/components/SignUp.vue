<template>
    <div>
          <img class="logo" alt="Vue logo" src="../assets/logo.png">
        <h1>Signup form</h1>
    </div>

    <div class="register">
        <input type="text" v-model="name" placeholder="Enter name"/>
        <input type="email" v-model="email" placeholder="Enter email"/>
        <input type="password" v-model="password" placeholder="enter password"/>
        <button :onclick="signUp">Sign Up</button>
        <p><router-link to="/login">Login</router-link></p>
    </div>
</template>

<script>
import axios from 'axios'
export default {
    name: 'Signup',
    setup () {
        return {
            name:'',
            email: '',
            password: '',
         
        }
    },
    methods:{
       async signUp(){
            // console.warn('Signup', this.name, this.email, this.password)
            let result = await axios.post("http://localhost:3000/user",{
                password:this.password,
                name:this.name,
                email:this.email
                });

                console.warn(result);
                if(result.status == 201) {
                   // alert("signup done");
                    localStorage.setItem('signUp-info',JSON.stringify(result.data));//store on the browser for easy access
                    this.$router.push({name:'Home'});
                }
        }
    },
    mounted(){
        //Prevent login user from visiting the signup page
        let user = localStorage.getItem('signUp-info');
        if(user){
            this.$router.push({name:'Home'});
        }
    }
}
</script>

<style>


</style>