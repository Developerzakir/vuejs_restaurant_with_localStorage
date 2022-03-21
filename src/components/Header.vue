<template>
    <div class="menu">

            <router-link to="/" >Home</router-link>
            <router-link to="/add" >Add Restaurant</router-link>
            <router-link to="/logout" @click="logout" >Logout</router-link>


    </div>
</template>

<script>
export default {
    name: 'Header',
    data (){
        return {}
    },

    methods:{
        logout(){
            localStorage.clear();
            this.$router.push({name: 'Login'})
        }
    }
}
</script>

<style  scoped>

</style>