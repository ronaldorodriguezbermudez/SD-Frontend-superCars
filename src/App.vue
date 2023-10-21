<template>
  <div id="app" class="container">
    <div class="row" style="margin-top: 15px">
      <router-link class="three columns button button-primary" to="/">Home</router-link>
      <router-link class="three columns button button-primary" to="/model">Models</router-link>
      <router-link class="three columns button button-primary" to="/designer">Designers</router-link>
      <router-link class="three columns button button-primary" to="/manufacturer">Manufacturers</router-link>
    </div>
    <router-view />
    <div class="row" style="margin-top: auto;"> <!-- Align to the bottom -->
      <div class="three columns"> <!-- Adjust column width as needed -->
        <button class="button button-primary" @click="runQueue('modelTasks')">Run Queues Models</button>
        <button class="button button-primary" @click="runQueue('designerTasks')">Run Queues Designers</button>
        <button class="button button-primary" @click="runQueue('manufacturerTasks')">Run Queues Manufacturers</button>
      </div>
    </div>
    <div class="row">
      <div class="twelve columns">
        <button disabled="disabled" class="button-primary">
          Copyright (c) 2023 - Ronaldo Rodriguez | Brandon Rodriguez
        </button>
      </div>
    </div>
    <div v-if="queueHasRun" class="row">
      <div class="twelve columns">
        <p>The queue has run.</p>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "App",
  data() {
    return {
      queueHasRun: false,
    };
  },
  methods: {
    runQueue(queueName) {
      fetch(`https://proyecto2-sd-backend.netlify.app/.netlify/functions/${queueName}`)
        .then((response) => {
          if (response.ok) {
            this.queueHasRun = true; // Set a flag to indicate the queue has run
            return response.text();
          } else {
            throw new Error("Request failed");
          }
        })
        .then((data) => {
          console.log(data);
        })
        .catch((error) => {
          console.error("Request error:", error);
        });
    },
  },
};
</script>
