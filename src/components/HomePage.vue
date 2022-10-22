<template>
    <HeaderPage/>
    <h1>Hello {{name}}, these are the resturants in the database</h1>
    <div>
        <table border="1">
            <tr>
                <td>Id</td>
                <td>Name</td>
                <td>Contact</td>
                <td>Address</td>
                <td>Actions</td>
            </tr>
            <tr v-for="item in resturant" :key='item.id'>
            <td>
                {{item.id}}
            </td>
            <td>
                {{item.name}}
            </td>
            <td>
                {{item.contact}}
            </td>
            <td>
                {{item.address}}
            </td>
            <td>
                <router-link :to="'/update/' + item.id">Update</router-link>
            </td>
            </tr>
        </table>
    </div>
</template>
<script>
import HeaderPage from './HeaderPage.vue'
import axios from 'axios'
    export default {
        name:'HomePage',
        data(){
            return {
                name:'',
                resturant:[],
            }
        },
        components:{
            HeaderPage
        },
        async mounted(){
            let user = localStorage.getItem('user-info')
            this.name = JSON.parse(user).name
            if(!user){
                this.$router.push({name:'SignUp'})
            }
            let result = await axios.get(`http://localhost:3000/resturants`)
            this.resturant = result.data
        }
    }
</script>
<style>
.table {
    border:black;
}
td {
    width:160px;
    height: 40px;
}
</style>