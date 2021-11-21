<template>
  <div>
    <div>
      <h1 v-if="display" id="demo">{{myname}}</h1>
      <button @click="toogle">Toogle</button>
    </div>
    <br><hr><br>
    <div>
      <div>
        <ul>
          <li v-for="e in error" :key="e.id">
            {{ e }}
          </li>
        </ul>
      </div>
      <h1>Form Validation</h1>
      <form @submit="loginfun">
        <input type="text" placeholder="UserName" v-model="username" />
        <br /><br />
        <input type="password" placeholder="Password" v-model="password" />
        <br /><br />
        <button type="submit">Login</button>
      </form>
    </div>
    <br><hr><br>
    <h1>Checkbox</h1>
    <input type="checkbox" id="one" value="one " v-model="checked">
    <label for="one">One </label>
    
    <input type="checkbox" id="one" value="Two " v-model="checked">
    <label for="one">Two </label>
    
    <input type="checkbox" id="one" value="Three " v-model="checked">
    <label for="one">Three </label>
    
    <input type="checkbox" id="one" value="four" v-model="checked">
    <label for="one">Four </label>

    <h4>Checked value: {{checked}}</h4>
    
    <br><hr><br>

    <h1>Radio button</h1>
    <input type="radio" id="one" value="one" v-model="pickd">
    <label for="one">One </label>
    <br>
    <input type="radio" id="two" value="two" v-model="pickd">
    <label for="one">Two </label>
    <br>
    <h4>Picked: {{pickd}}</h4>

    <br><hr><br>
    <h1>Select</h1>
    <select v-model="select" >
      <option disabled value="">Select one value</option>
      <option value="A">A</option>
      <option value="B">B</option>
      <option value="C">C</option>
      <option value="D">D</option>
    </select>
    <span style="inline-block">Selecte: {{select}}</span>
    <br><hr><br>

    <h1>Select Multiple</h1>
    <select v-model="selected" multiple>
      <option disabled value="">Select one value</option>
      <option value="A">A</option>
      <option value="B">B</option>
      <option value="C">C</option>
      <option value="D">D</option>
      <option value="E">E</option>
      <option value="F">F</option>
    </select>
    <span style="inline-block">Selecte: {{selected}}</span>
    <br><hr><br>
    <h1>Dynamically Selected</h1>
    <select v-modal="dynamicSelected">
      <option v-for="option in options" v-bind:key="option.value" v-bind:value="option.value">{{option.text}}</option>
    </select>
    <span>Selected: {{dynamicSelected}}</span>
    <br><hr><br>
    <h1>Feetch Api Data</h1>
    <table border="1">
      <tr border="1">
        <th>ID</th>
        <th>Name</th>
        <th>Email</th>
        <th>Username</th>
        <th>Pgon</th>
      </tr>
      <tr v-for="user in this.list" :key="user.id">
        <td> {{ user.id  }} </td>
        <td> {{ user.name  }} </td>
        <td> {{ user.email  }} </td>
        <td> {{ user.username  }} </td>
        <td> {{ user.phone  }} </td>
      </tr>
      
    </table>
    <br><hr><br>

    <br><hr><br>

  </div>
</template>

<script>
import Vue from 'vue';
import VueAxios from 'vue-axios';
import axios from 'axios';

Vue.use(VueAxios,axios)


export default {
  name: "formvalid",
  mounted(){
    Vue.axios.get('https://jsonplaceholder.typicode.com/users')
    .then(resp=>{
      this.list=resp.data;
      console.log(this.list)
    })
  },
  data() {
      return {
        dynamicSelected:'A',
        list:undefined,
      options:[
        {text:'One', value:'A'},
        {text:'two', value:'B'},
        {text:'three', value:'C'},
        {text:'four', value:'D'}
      ],
      
      selected:[],
      select:'',
      checked:[],
      pickd:null,
      myname:'Asjad Ali',
      display:true,
      error: [],
      username: null,
      password: null,
    };
  },
  methods: {
    toogle(){
      this.display=!this.display;
    },
    loginfun(e) {
      // console.log(this.username,this.password);
      this.error = [];
      if (this.username && this.password) {
        console.warn("No Error Login Successful");
      }
      if (!this.username) {
        this.error.push("Username requird");
      }
      if (!this.password) {
        this.error.push("Password requird");
      }
      console.warn(this.error);
      e.preventDefault();
    },
  },
    // beforeCreate(){
    //   this.myname='Asjad in Before Created'
    //   console.log("Before Created",this.myname)
    // },
    // created(){
    //   this.myname='Asjad in Created'
    //   console.log("created",this.myname)
    // },

    // beforeMount(){
    //   console.log("brfore mOunt",document.getElementById("demo"))
    // },
    // mounted(){
    //   console.log("Mounted",document.getElementById("demo"))
    // },
    // beforeUpdate(){
    //   alert("before mount")
    //   console.log("before Update",this.myname)
    // },
    // updated(){
    //   alert("mount")
    //   console.log("Updated",this.myname)
    // },

    // beforeDestroy(){
    //   alert("before destroye")
    //   console.log("before destroye",this.myname)
    // },
    // destroyed(){
    //   alert("destroyed")
    //   console.log("destroyed",this.myname)
    // }
};
</script>

<style></style>
