<template>
  <div id="app" class="container">
    <div class="row" style="margin-top: 15px">
      <router-link class="three columns button button-primary" to="/">Home</router-link>
      <router-link class="three columns button button-primary" to="/model">Models</router-link>
      <router-link class="three columns button button-primary" to="/designer">Designers</router-link>
      <router-link class="three columns button button-primary" to="/manufacturer">Manufacturers</router-link>
    </div>
    <router-view />
    <div class="row" style="margin-top: 15px">
      <button class="three columns button button-primary" @click="runQueue('modelTasks')">Run Queues Models</button>
      <button class="three columns button button-primary" @click="runQueue('designerTasks')">Run Queues Designers</button>
      <button class="three columns button button-primary" @click="runQueue('manufacturerTasks')">Run Queues Manufacturers</button>
    </div>
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
  methods: {
    runQueue(queueName) {
      // Perform a fetch request to the specified URL
      fetch(`https://proyecto2-sd-backend.netlify.app/.netlify/functions/${queueName}`)
        .then((response) => {
          if (response.ok) {
            return response.text();
          } else {
            throw new Error("Request failed");
          }
        })
        .then((data) => {
          // Handle the response data as needed
          console.log(data);
        })
        .catch((error) => {
          // Handle errors, e.g., show an error message to the user
          console.error("Request error:", error);
        });
    },
  },
};
</script>
