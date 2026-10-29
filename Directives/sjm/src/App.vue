<script setup>
import {ref}  from "vue";
import users from "./users.json";

const username=ref("");
const password=ref("");
const currentUser=ref(null);
const showPassword=ref(false);

function login(){
  currentUser.value=users.find((user)=>
  user.username===username.value && user.password===password.value
  )||null;
  if(!currentUser.value){
    alert("Invalid username or password");
  };
};

function logout(){
  currentUser.value=null;
  username.value="";
  password.value="";
  showPassword.value=false;
};
</script>
<template>
  <div>
    <h3>🔐 Role-Based Login System</h3>
    <p>Login to access you dashboard</p>
    <div v-if="!currentUser">
      <input type="text" placeholder="Enter username" v-model="username">
      <input :type="showPassword ? 'text':'password'" placeholder="Enter password" v-model="password">
      <label><input type="checkbox" v-model="showPassword">show password</label>
      <button @click="login">Login</button>
    </div>
    <div v-else>
      <h3> Welcome, {{ currentUser.username }}</h3>
      <p>Role :<span>{{currentUser.role }}</span></p>
      <div v-if="currentUser.role=='Admin'">
        <h1>Admin Dashboard></h1>
        <ul>
          <li v-for="item in ['Maneg users','View reports','Setting']":key="item">
            {{ item }}
          </li>
>        </ul>
        
      </div>
      <div v-else-if="currentUser.role=='Teacher'">
        <h1>Teacher Dashboard></h1>
        <ul>
          <li v-for="item in ['Maneg users','View reports','Setting']":key="item">
            {{ item }}
          </li>
>        </ul>
      </div>
      <div v-else>
        <h1>Student Dashboard></h1>
        <ul>
          <li v-for="item in ['Maneg users','View reports','Setting']":key="item">
            {{ item }}
          </li>
>        </ul>
      </div>
      <div v-show="currentUser.role=='Admin'">
        <p>Only admin can view this message</p>
      </div>
      <button @click="logout">Logout</button>
    </div>
  </div>
</template>
