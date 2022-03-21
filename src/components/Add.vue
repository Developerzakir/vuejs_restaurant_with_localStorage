<template>
<Header />
    <div>
        <h1>Welcome to Add Restaurant Page</h1>

        <form action="" class="add">
            <input type="text" v-model="restaurant.name" name="name" placeholder="Enter Restaurant Name ">
            <input type="text" v-model="restaurant.address" name="address" placeholder="Enter Address">
            <input type="text" v-model="restaurant.contact" name="contact" placeholder="Enter Contact">
           <button type="button" @click="addRestaurant">Add New Restaurant </button>
        </form>

    </div>
</template>

<script>
import Header from './Header.vue'
import axios from 'axios'

export default {
    name: 'Add',
    components:{
        Header
    },

    data () {
        return {
            restaurant:{
                name: '',
                contact: '',
                address: ''

            }
           
        }
    
    },

    methods:{

        async addRestaurant()
        {
            console.warn(this.restaurant);
            const result = await axios.post("http://localhost:3000/restaurant",{
                name: this.restaurant.name,
                address: this.restaurant.address,
                contact: this.restaurant.contact
            });
            if(result.status==201)
            {
                this.$router.push({name: 'Home'})

            }
            console.warn("result", result)

        }

    },

    mounted(){
        let user = localStorage.getItem('user-info');
        if(!user)
        {
            this.$router.push({name: 'SignUp'})
        }
    }


}
</script>

<style lang="scss" scoped>

</style>