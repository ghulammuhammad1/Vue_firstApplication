<template>
    <div>
        <label>User Form</label><br><br> 
        <input type="text" placeholder="Enter the name" v-model="users.name"/><br><br>
        <input type="text" placeholder="Enter the email" v-model="users.email"/><br><br>
        
        <p>Hobies</p>
        <input type="checkbox" value="sports" id="sports" v-model="users.hobbies"/>
        <label for="sports">Sports</label>
        <input type="checkbox" value="travel" id="travel" v-model="users.hobbies"/>
        <label for="travel">Travel</label><br>
        <p>Gender</p>
        <input type="radio" value="male" id="male" v-model="users.gender"/>
        <label for="male">Male</label>
        <input type="radio" value="female" id="female" v-model="users.gender"/>
        <label for="female">Female</label><br><br> 
        <button v-on:click="submitData()" >Submit</button>
    </div>
</template>
<script>
export default {
    name:"Form",
    data(){
       return{
            users:{
                name:null,
                email:null,
                hobbies:[],
                gender:null
            }
       }
    },
    methods:{
        submitData(){
            console.warn("submitted",this.users)
        }
    }
}
</script>