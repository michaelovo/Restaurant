<template>
<Header/>
    <div>
        <h2>Update resturant</h2>
    </div>

    <div class="add">
        <form>
           
            <input type="text" name="name" v-model="resturant.name" placeholder="Enter Restaurant name">
            <input type="text" name="address" v-model="resturant.address" placeholder="Enter Restaurant Address">
            <input type="text" name="contact" v-model="resturant.contact" placeholder="Enter Restaurant Contact number">
          
            <button type="button" :onclick="updateRestaurant" class="add">Update</button>
        </form>
    </div>
</template>

<script>
import Header from './Header.vue';
import axios from 'axios';
    export default {
        name: 'Update',
        components:{
            Header
        },
        data(){
            return {
                resturant:{
                    name:'',
                    contact: '',
                    address: '',
                }
            }

        },
        methods: {
            async updateRestaurant(){
                const result = await axios.put("http://localhost:3000/resturants/"+this.$route.params.id,{
                    name:this.resturant.name,
                    contact:this.resturant.contact,
                    address:this.resturant.address
                });

                if(result.status == 200){
                    this.$router.push({name:'Home'});
                }
            }

        },
       async mounted(){
            //prevent visiting homepage if not login
            let user = localStorage.getItem('signUp-info');
            if(!user) {
                this.$router.push({name:'SignUp'});
            }

                 
                const result = await axios.get("http://localhost:3000/resturants/"+this.$route.params.id)
                this.resturant = result.data;
               // console.warn(result);
            //console.warn(this.$route.params.id);
        }
    }
</script>

<style scoped>

</style>