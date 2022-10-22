<template>
    <HeaderPage/>
    <h1>Add New Resturant</h1>
    <form class="add">
        <input type="text" name="name" v-model="resturant.name" placeholder="Name">
        <input type="text" name="contact" v-model="resturant.contact" placeholder="Contact">
        <input type="text" name="address" v-model="resturant.address" placeholder="Address">
        <button type="button" v-on:click="addResturant">Add new Resturant</button>
    </form>
</template>
<script>
import HeaderPage from './HeaderPage.vue'
import axios from 'axios'
    export default {
        name:'AddPage',
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
        methods:{
            async addResturant(){
                const result = await axios.post(`http://localhost:3000/resturants`,{
                    name:this.resturant.name,
                    contact:this.resturant.contact,
                    address:this.resturant.address
                })
                if(result.status==201){
                    this.$router.push({name:'HomePage'})
                }
            }
        },
        mounted(){
            let user = localStorage.getItem('user-info')
            if(!user){
                this.$router.push({name:'SignUp'})
            }
        }
    }
</script>