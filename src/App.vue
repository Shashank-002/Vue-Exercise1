<template>
  <div>
   <userDetail/>
  </div>
 </template>
 
 <script>
 import userDetail from './components/userDetail.vue'
 
 export default {
   name: 'App',
   components: {
     userDetail,
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
   margin-top: 60px;
 }
 </style>
 