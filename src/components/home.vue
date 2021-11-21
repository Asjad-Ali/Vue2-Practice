<template>
    <div class="home">
    <h1>Home Page</h1>
    <!-- <input type="text" v-model="name">
    <button  v-on:click="updateTitle">Update the title</button> -->
        <subhome />
    </div>
    
</template>

<script>
import subhome from './subhome';


export default{
    name:'Home',
    components:{
        subhome
    },
    // data(){
    //     return{
    //         name:'Asjad'
    //     }
    // },
    // methods:{
    //     updateTitle(){
    //         this.$emit('changeTitle',this.name)
    //     }

    // }
}
</script>




<style >
.home{
    background-color:#6595;
    height: 500px;
    
}
</style>