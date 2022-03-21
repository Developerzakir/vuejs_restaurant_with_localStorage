<template>
<Header />
    <div>
         <h1>Update Restaurant Page</h1>
        <form  class="update">
            <input type="text" v-model="restaurant.name" name="name" placeholder="Enter Restaurant Name ">
            <input type="text" v-model="restaurant.address" name="address" placeholder="Enter Address">
            <input type="text" v-model="restaurant.contact" name="contact" placeholder="Enter Contact">
           <button type="button" @click="updateRestaurant">Update Restaurant </button>
        </form>

    </div>
</template>

<script>
import Header from './Header'
import axios from 'axios'

export default {
    name: 'Update',
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

        async updateRestaurant()
        {
            console.warn(this.restaurant);
            const result = await axios.put("http://localhost:3000/restaurant/"+this.$route.params.id,{
                name: this.restaurant.name,
                address: this.restaurant.address,
                contact: this.restaurant.contact
            });
            if(result.status==200)
            {
                this.$router.push({name: 'Home'})

            }
            console.warn("result", result)

        }

    },

   async  mounted(){
        let user = localStorage.getItem('user-info');
        if(!user)
        {
            this.$router.push({name: 'SignUp'})
        }

        const result = await axios.get('http://localhost:3000/restaurant/'+this.$route.params.id)

       
        console.warn(result.data)
        this.restaurant = result.data
     }
}
</script>

<style lang="scss" scoped>

</style>