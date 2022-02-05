<template>
<Header/>
    <div>
        <h2>Add resturant</h2>
    </div>
    <div class="add">
        <form>
           
            <input type="text" name="name" v-model="resturant.name" placeholder="Enter Restaurant name">
            <input type="text" name="address" v-model="resturant.address" placeholder="Enter Restaurant Address">
            <input type="text" name="contact" v-model="resturant.contact" placeholder="Enter Restaurant Contact number">
          
            <button type="button" :onclick="addRestaurant" class="add">Add</button>
        </form>
    </div>
</template>

<script>
import Header from './Header.vue';
    export default {
        name: 'Add',
        data(){
            return {
                resturant:{
                    name:'',
                    contact: '',
                    address: '',
                }
            }
        },
        methods:{
            addRestaurant(){
                console.warn(this.resturant);
            }
        },
        components:{
            Header
        },
        mounted(){
            //prevent visiting homepage if not login
            let user = localStorage.getItem('signUp-info');
            if(!user) {
                this.$router.push({name:'SignUp'});
            }
        }
    }
</script>

<style scoped>

</style>