<template>
    <div class="home"> 
        <h1>This is Home Component</h1>
        <Users />
        <Products/>
    </div>
</template>

<script>
import Users from './Users.vue'
import Products from './Products.vue'
export default {
    name:"Home",
    components:{
        Users,
        Products
    }
}
</script>

<style scoped>
.home{
    background-color:brown;
    height: 500px;
}
</style>