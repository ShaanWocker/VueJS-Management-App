<template>
    <HeaderPage/>
    <h1>Update Resturant Details</h1>
    <form class="add">
        <input type="text" name="name" v-model="resturant.name" placeholder="Name">
        <input type="text" name="contact" v-model="resturant.contact" placeholder="Contact">
        <input type="text" name="address" v-model="resturant.address" placeholder="Address">
        <button type="button" v-on:click="updateResturant">Update Resturant</button>
    </form>
</template>
<script>
import HeaderPage from './HeaderPage.vue'
import axios from 'axios'
    export default {
        name:'UpdatePage',
        components:{
            HeaderPage
        },
        data(){
            return {
                resturant : {
                    name:'',
                    contact:'',
                    address:''
                }
            }
        },
        methods: {
            async updateResturant(){
                const result = await axios.put(`http://localhost:3000/resturants/` + this.$route.params.id,{
                    name:this.resturant.name,
                    contact:this.resturant.contact,
                    address:this.resturant.address
                })
                if(result.status==200){
                    this.$router.push({name:'HomePage'})
                }
            }
        },
        async mounted(){
            let user = localStorage.getItem('user-info')
            if(!user){
                this.$router.push({name:'SignUp'})
            }

            const result = await axios.get(
                'http://localhost:3000/resturants/' + this.$route.params.id
                )
                this.resturant = result.data
        }
    }
</script>