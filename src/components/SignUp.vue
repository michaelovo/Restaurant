<template>
    <div>
          <img class="logo" alt="Vue logo" src="../assets/logo.png">
        <h1>Signup form</h1>
    </div>

    <div class="register">
        <input type="text" v-model="name" placeholder="Enter name"/>
        <input type="email" v-model="email" placeholder="Enter email"/>
        <input type="password" v-model="password" placeholder="enter password"/>
        <button :onclick="signUp">Login</button>
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
                passord:this.password,
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