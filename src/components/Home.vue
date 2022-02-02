<template>
    <div>
        <h2>hello</h2>
    </div>
</template>

<script>
    export default {
        name: 'Home',
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