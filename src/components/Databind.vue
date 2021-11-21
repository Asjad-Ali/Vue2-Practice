<template>
    <div>
        <h1>Props parent to child</h1>
        <h1 v-for="namme in usersData" :key="namme.id">{{namme.id}}-- 
            {{namme.name}}--{{namme.email}}</h1>
        <!-- <h2>{{message}}</h2>
        <input type="text" v-model="message" > -->
    </div>
</template>




<script>
export default {
    name:'Databind',
    props:['usersData']
    // data(){
    //     return{
    //         message:"hi"
    //     }
    // }
}
</script>