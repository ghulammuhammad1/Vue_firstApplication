
<template>
    <div>
        <h1 v-if="show">Events in VueJS</h1>
        <!-- <h1 v-else>Else part</h1> -->
        <button v-on:click="display()">Toggle</button>
        <table border="2">
            <tr>
                <td>ID</td><td>Name</td><td>Email</td>
            </tr>
            <tr v-for="user in users" :key="user.id"> 
                <td>{{user.id}}</td><td>{{user.name}}</td><td>{{user.email}}</td>
            </tr>
        </table>
    </div>
</template>

<script>
import Vue from 'vue'
import { BootstrapVue } from 'bootstrap-vue'

Vue.use(BootstrapVue)

export default{
    
    name:'Events',
    props:{
        data:String
    },
    methods:{
        onclick(){
            console.log('Hey this is method');
        },
        display(){
            this.show=!this.show
        }
    },
    data(){
        return{
            show:true,
            users:[
                {id:1,name:"GM",email:"gm@123"},
                {id:2,name:"suhail",email:"gm@123"},
                {id:3,name:"ali",email:"gm@123"},
                {id:4,name:"tariq",email:"gm@123"}

            ]
        }
    }
}
</script>
