<template>
    <div>
    <b-form @submit="submitData" @reset="onReset">
      <b-form-group
        id="input-group-1"
        label="Email address:"
        label-for="input-1"
        description="We'll never share your email with anyone else."
      >
        <b-form-input
          id="input-1"
          v-model="users.email"
          type="email"
          placeholder="Enter email"
          required
        ></b-form-input>
      </b-form-group>

      <b-form-group id="input-group-2" label="Your Name:" label-for="input-2">
        <b-form-input
          id="input-2"
          v-model="users.name"
          placeholder="Enter name"
          required
        ></b-form-input>
      </b-form-group>
      <br>
      <b-button type="submit" variant="primary">Submit</b-button>
      <b-button type="reset" variant="danger">Reset</b-button>
    </b-form>

        <br>
        <button v-on:click="display()">Get Data</button><br><br>
         <b-table striped hover :items="data" v-if="data"></b-table>
        Enter the ID to seach: <input type="text" placeholder="Enter id" v-model="id"/>
        <button v-on:click="search()">Search</button>

       <br><br>
    </div>
</template>
<script>
// import axios from 'axios'
export default {

    name:"FormValidation",
    data(){
       return{
            users:{
                name:"",
                email:""
            },
            error:{
                name:"",
                email:""
            },
            data:null,
            id: undefined
       }
    },
    methods:{
        submitData(e){
            if(this.users.name && this.users.email){
                console.warn("DATA:", this.users)
            }
            if(!this.users.name){
               this.error.name="*Name is Required"
            }
            else{
                this.error.name="";
            }
            if(!this.users.email){
                this.error.email="*Email is Required"
            }
            else{
                this.error.email="";
            }
            console.warn(this.error);
            alert(JSON.stringify(this.users));
            this.axios.post('http://localhost:8888/person', this.users )
            .then(response => (console.warn(response)))
            e.preventDefault();
            
        },
        onReset(event) {
        event.preventDefault()
        // Reset our form values
        this.users.email = ''
        this.users.name = ''
      },
        display(){
            this.axios.get('http://localhost:8888/person')
            .then(data=>(this.data=data.data))
        },
        search(){
            console.warn(this.id)
            this.axios({
                method:'post',
                url:'http://localhost:8888/person/search',
                data:this.id,
            headers:{'Content-Type': 'application/json', 'charset': 'utf-8'},
            })
            .then(data=>(console.warn(data)))
        }
    },
    
    mounted () {
    
  }
}
</script>
<style>
.name{
    color: red;
}
</style>