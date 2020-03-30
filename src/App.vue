<template>
  <div id="app">
   <div style="margin-top: 100px" class="container">
<div class="container">
  <div class="row">
     <div class="col-8"><div class="form-group">
    <label for="example1"><b>Name Input</b></label>
    <input type="text" id="example1" class="form-control"  placeholder="username" v-model="username" ></div>
    </div>
    <div class="col-4">
      <button type="submit" class="btn btn-success" @click="addUser">Add User</button>
    </div>
  </div>
</div>
         
     <!-- <b-button variant="success"  @click="addUser">Add User</b-button> -->
  
  
        <!-- <input type="text" placeholder="username" v-model="username" /> -->
        <!-- <button type="submit" @click="addUser">add</button> -->
        <div class="container">
  <div class="row">
    <div class="col-sm-10">
       <ul class="list-group">
            <li class="list-group-item" v-for="user in users" :key="user.id" right> {{user.name}}
            <button type="submit" @click="removeUser" class="btn" left>Del</button>

            </li>
        </ul>
        </div>
    </div>
</div>
           <!-- <ul class="list-group">
            <li class="list-group-item" v-for="user in users" :key="user.id" right> {{user.name}}
            <button type="submit" @click="removeUser" class="btn" left>Del</button>

            </li>
        </ul> -->
    </div>
  </div>
</template>

<script>
import axios from "axios";

export default {
    data(){
        return{
            users: [],
            username: ''
        }
    },
    methods:{
         addUser(){
             let username = {
                name: this.username
             }
              this.users.unshift(username)
             this.username = ""
        },
         removeUser(){
             let username = {
                name: this.username
             }
              this.users.shift(username)
             this.username = ""
        }
    },
    async created() {
        let fetchUsers = await axios.get("https://jsonplaceholder.typicode.com/users");
        console.log(fetchUsers);

        this.users = fetchUsers.data;
    }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  /* display: flex; */
  /* border: 1px solid black */
}
.list-group-item{
        /* display: flexbox;
        justify-content: center; */
        margin-top: 30px;
    }
    .btn{
        background-color: red;
        color: aliceblue;
        float: left;
        margin-top: 30px;
        border-radius: 30px
    }
</style>
