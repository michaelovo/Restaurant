<template>
<Header/>
    <div>
        <h2>hello {{user_name}}</h2>
    </div>
    <div class="center">
        <table id="example" class="table table-striped" style="width:100%">
            <thead>
                <tr>
                    <th>SN</th>
                    <th>Name</th>
                    <th>Phone</th>
                    <th>Address</th>
                    <th>Action</th>
                </tr>
            </thead>
            <tbody>
                <tr v-for="item in resturants" :key="item.id">
                    <td>{{item.id}}</td>
                    <td>{{item.name}}</td>
                    <td>{{item.contact}}</td>
                    <td>{{item.address}}</td>
                    <td>
                        <router-link :to="'/update/' + item.id">
                            <a class="btn btn-primary">Edit</a>
                        </router-link>
                        <button  type="button" class="btn btn-danger" v-on:click="deleteRestaurant(item.id)">Delete</button>
                    </td>
                </tr>
                
            </tbody>
        </table>
    </div>
</template>

<script>
import Header from './Header.vue';
import axios from 'axios';
    export default {
        name: 'Home',
        data () {
            return{

                user_name:'',
                resturants: [],
            }
        },
        components:{
            Header
        },
         methods: {
            async deleteRestaurant(id){
                let result = await axios.delete("http://localhost:3000/resturants/"+id);

                if(result.status == 200){
                    //delete and auto-load data function call
                    this.loadData();
                }
            },
            
            async loadData(){
                //prevent visiting homepage if not login
                let user = localStorage.getItem('signUp-info');
                this.user_name = JSON.parse(user).name;
                if(!user) {
                    this.$router.push({name:'SignUp'});
                }

                let result = await axios.get("http://localhost:3000/resturants");
                this.resturants = result.data;
                //console.warn(result);
            }

        },
       async mounted(){
            this.loadData();
        }
    }
</script>

<style>
    /* td{
        width: 160px;
        height: 14px;
        text-align: left;
    } */
</style>