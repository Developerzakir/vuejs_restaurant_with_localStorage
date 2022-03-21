<template>
    <div>
        <img src="../assets/signup.png" alt="">
        <h1>Sign Up Page</h1>

        <div class="register">
            <input type="text" v-model="name" placeholder="Enter Name"> <br/>
            <input type="text" v-model="email" placeholder="Enter Email">  <br/>
            <input type="password" v-model="password" placeholder="Enter Password"> <br/>
            <button @click="SignUp">SignUp</button>
        </div>

        <router-link to="/login">Go Login Page</router-link>

    </div>
</template>

<script>
import axios from 'axios'
export default {
    name: 'SignUp',
    data() {
        return {
            name: '',
            email: '',
            password: ''
        }
    },

    methods: {
        async SignUp(){
            let result = await axios.post("http://localhost:3000/users", {
                name: this.name,
                email: this.email,
                password: this.password
            });

            console.warn(result);
            if(result.status==201){
                
                localStorage.setItem('user-info', JSON.stringify(result.data))
                this.$router.push({name: 'Home'})
            }
        }
    },

    mounted(){
        let user = localStorage.getItem('user-info');
        if(user)
        {
            this.$router.push({name: 'Home'})
        }
    }
}
</script>

<style  scoped>



</style>