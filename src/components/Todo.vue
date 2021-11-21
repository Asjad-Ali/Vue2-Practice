<template>
  <div>
    <div class="row d-flex flex-column m-3 pt-3 justify-content-evenly">
        <div class="col"><h1>To-Do List</h1></div>
        <div class="col"><h3>What need to be done ?</h3></div>
        <div class="col"><input type="search" name="" id="inputDataAdd" 
        class="w-50" placeholder="Enter the title for Add" v-model="addTitle"></div>
        <div class="col"><button class="btn btn-dark mt-2 w-50" 
        @click="addData()">Add</button></div>
        <div class="col mt-3">
          <h3>Total {{list.length}} record in Todo List</h3>
        </div>
    </div>
    
    <div v-for="(user,index) in list" :key="user.index">
      <div
        class="card m-auto p-0"
        style="width: 42rem; border: 2px solid green"
      >
        <div class="card-body text-start">
          <div class="row m-0">
            <div class="col-2 showDiv ps-3"><b>Status</b></div>
            <div class="col-2 showDiv ps-1 ms-1"><b>ID</b></div>
            <div class="col-3 showDiv "><b>Title</b></div>
          </div>
          <div class="row">
            <div class="col-2 showDiv ms-4 ps-3"><div><input v-if="user.completed" checked  type="checkbox" ><input v-else type="checkbox" ></div></div>
            <div class="col-1 showDiv ">{{ user.id }}</div>
            <div class="col-8 showDiv">{{ user.title }}</div>
          </div>
        </div>
        <div class="row mb-2">
          <div class="col"> 
             <button class="btn btn-outline-success  w-75" v-b-modal.edit-Modal @click="editData(index)">Edit</button>
          </div>
          <div class="col">
            <button class="btn btn-danger w-75" v-on:click="deleteUsers(index)">Delete</button>
          </div>
        </div>
      </div>
      <br />
    </div>
        <!-- <b-modal id="edit-Modal" size="sm"  centered hide-footer  title="Update Data" cancel->
      <input type="text"  class="w-100" v-model="this.addTitle">
      <b-button   variant="primary" @click="editData(index)" size="sm">Small Button</b-button>
    </b-modal> -->

      <div class="text-center">
            <b-modal visible centered  ref="my-modal" size="sm" id="edit-Modal" header="test" title="Update Title" hide-footer  no-close-on-backdrop no-close-on-esc >
                <div class="col-12">
                    <p class="col-12">Enter title for Update</p>
                </div>
                <div class="col-12">
                    <div class="ml-2 mr-2">
                    <b-form-input  type="text" id="pin-input" v-model="editTitle "  required></b-form-input>
                    </div>
                </div>
                <div class="col-12 text-center">
                    <b-button variant="primary" size="sm" class="mt-2 mr-2"  @click="update()" v-on:click="$bvModal.hide('bv-modal-example')">Update</b-button>
                </div>
            </b-modal>
        </div>

    
  </div>
</template>

<script>
import Vue from "vue";
import VueAxios from "vue-axios";
import axios from "axios";

Vue.use(VueAxios, axios);

export default {
  name: "Todo",
  data() {
    return {
      list: undefined,
      addTitle:"",
      editTitle: "",
      editTitleIndex:0,
      totalStatus:0,
      completedStatus: 0,
    };
  },
  methods: {
    getUsers() {
      this.axios
        .get("https://jsonplaceholder.typicode.com/todos")
        .then((resp) => {
          this.list = resp.data;
        });
    },
    deleteUsers(index) {
      const con = confirm(
        "If you want to delete data of"+ this.list[index].title + " click OK if not then cancel"
      );
      if (con) {
        this.list.splice(index, 1);
      }
    },
    editData(index) {
      this.editTitle = this.list[index].title;
      this.editTitleIndex=index
    },
    update(){
        if(this.editTitle != ""){
        this.list[this.editTitleIndex].title=this.editTitle;
        this.editTitle=null;
        
      }
      this.hideModal();
      this.checkStatus();
    },
    hideModal() {
        this.$refs['my-modal'].hide();
    },
    addData(){
      let len=this.list.length;
      if(this.addTitle === "") {alert("Please Enter the Title First");}
      else{
        this.list.unshift({
        id:len,
        title: this.addTitle,
        completed: true,
      })
      }
    },
  },
  mounted() {
    this.getUsers();
  },
};
</script>

<style scoped>
.showDiv {
  margin: 5px;
  padding: 0;
}
#inputDataAdd{
  border-radius: 8px;
  padding: 2px 5px;
}
</style>
