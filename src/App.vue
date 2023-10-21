<template>
  <div id="app" class="container">
    <div class="row"  style="margin-top: 15px">
      <router-link class="three columns button button-primary" 
        to="/">Home</router-link>
      <router-link class="three columns button button-primary" 
        to="/model">Models</router-link>
      <router-link class="three columns button button-primary" 
        to="/designer">Designers</router-link>
      <router-link class="three columns button button-primary" 
        to="/manufacturer">Manufacturers</router-link>
    </div>
   <router-view />
    <div class="row">
      <button disabled="disabled" class="twelve columns button-primary">
        Copyright (c) 2023 - Ronaldo Rodriguez | Brandon Rodriguez
      </button>
    </div>
  </div>
  </template>
  
  <script>
  export default {
    name: "App",
  };
  </script>