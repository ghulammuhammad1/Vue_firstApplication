<template>
    <div class="greetings">
        <h1>{{message}}</h1>
        <input type="text" v-model="message"/>
        <button v-on:click="updateTitle">Change Title</button>
    </div>
</template>


<script>
export default {
    name:'Greetings',
    data(){
        return{
            message:"Hello"
        }
    },
    methods:{
        updateTitle(){
            this.$emit('changeTitle','Props has been passed')
        }
    }
}
</script>