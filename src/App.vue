<template>
  <div id="app">
    <h1>Main App</h1>
    <!-- <div>
      <nav>
        <ul style="margin-bottom:0px;">
          <li>
            <router-link class="listItem" to="/">Todo</router-link>
          </li>
          <li>
            <router-link class="listItem" to="/weather">Weather</router-link>
          </li>
        </ul>
      </nav>
    </div>-->

    <!-- <router-view></router-view>  -->



    <!-- <h1>{{title | UseCase}}</h1> -->
    <!-- <home v-on:changeTitle="updateTitle($event)" /> -->
    <!-- <Databind v-bind:name="users"/> -->
    <!-- <img src="./assets/logo.png" alt="vue logo"> -->
    <!-- <HelloWorld msg="Welcome to Your Vue.js App"/> -->
    <!-- <hello message="hello Vue!"/> -->
    <!-- <formvalid  /> -->
    <!-- <Todo /> -->
    <!-- <weather /> -->
    <!-- <slot /> -->
    <!-- <slots /> -->


    <!-- <slots>
      <template v-slot:header>
      <h1>Asjad Ali</h1>
    </template>
      <template v-slot:content>
      <p>Lorem ipsum dolor sit, amet consectetur adipisicing elit. Alias recusandae quod accusamus eveniet at! Neque, maxime, exercitationem natus qui cupiditate dolorum cum vitae labore iste quaerat, quas culpa! In, dicta!</p>
    </template>
      <template v-slot:footer>
      <img style="height:200px;width:260px" src="./assets/weather.jpg" alt="">
      <b-button class="mt-2" variant="primary">Button</b-button>
    </template>
    </slots> -->
    <DynamicComp />

    
  </div>
  
</template>

<script>
// import Databind from './components/Databind.vue'
// import home from './components/home.vue'
// import HelloWorld from './components/HelloWorld.vue'
// import formvalid from './components/formvalid.vue'
// import Todo from './components/Todo.vue'
// import weather from './components/weather.vue'
// import slot from './components/slot.vue'
// import slots from './components/slots.vue'
import DynamicComp from './components/DynamicComp.vue'


export default {
  name: 'App',
  components: {
    // Databind
    // home
    // HelloWorld
    // formvalid
    // Todo,
    // weather,
    // Slot
    // slots
    DynamicComp
  },
  data(){
    return{
        // title:'Main App Page',
        // usersData:[
        // {id:1,name:"Asjad Ali NEW ",email:"Asjad@gmail.com",des:"Frontend Developer"},
        // {id:2,name:"Ali Raza NEW",email:"Ali@gmail.com",des:"Frontend Engineer"},
        // {id:3,name:"Amjad Ali NEW",email:"Amjad@gmail.com",des:"wordpress Developer"},
        // {id:4,name:"Ghafar Ali NEW",email:"Gafarali@gmail.com",des:"Java Developer"}
        // ]
      // }
  }
  // methods:{
  //   updateTitle(titl){
  //     this.title=titl
  //   }
}
}
</script>

<style>
#app {
  background-color: aquamarine;
  text-align: center;
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  color: #2c3e50;
  
}

nav{
  background-color: rgb(13, 12, 14);
  padding: 0px;
  margin: 0px;
}
li{
  size: 30px;
    display: inline-block;
}
.listItem{
  color: white;
  text-decoration: none!important;
  margin: 20px;
  list-style: none;
}

</style>