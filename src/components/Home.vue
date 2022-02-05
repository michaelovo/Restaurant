<template>
<Header/>
    <div>
        <h2>hello</h2>
    </div>
</template>

<script>
import Header from './Header.vue';
    export default {
        name: 'Home',
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