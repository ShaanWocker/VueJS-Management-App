<template>
    <HeaderPage/>
    <h1>Hello {{name}}, these are the resturants in the database</h1>
    <div>
        <table>
            <tr>
                <td>Id</td>
                <td>Name</td>
                <td>Contact</td>
                <td>Address</td>
                <td>Update</td>
                <td>Delete</td>
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
            <td>
                <button v-on:click="deleteResturant(item.id)">Delete</button>
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
        methods:{
            async deleteResturant(id){
                let result = await axios.delete(`http://localhost:3000/resturants/` + id)
                if(result.status==200){
                    this.loadData()
                }
            },
            async loadData(){
                let user = localStorage.getItem('user-info')
                this.name = JSON.parse(user).name
                if(!user){
                    this.$router.push({name:'SignUp'})
                }
            let result = await axios.get(`http://localhost:3000/resturants`)
            this.resturant = result.data
        }
        },
        async mounted(){
            this.loadData()
        }
    }
</script>
<style>
table {
    border:1px solid #000000;
    margin-left: auto;
    margin-right: auto;
}
td {
    width:160px;
    height: 40px;
    border:1px solid #000000;
}
</style>