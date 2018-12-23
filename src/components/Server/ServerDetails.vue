<template>
  <div class="col-xs-12 col-sm-6">
    <p>Server #{{this.id}} - Status is {{this.status}}</p>
    <!-- TODO: add a button to return server status to normal -->
    <button @click="resetStatus">Reset server status</button>
  </div>
</template>

<script>
import { eventBus } from "../../main.js";

export default {
  data() {
    return {
      id: 1,
      status: "Unknown"
    };
  },
  methods: {
    resetStatus() {
      this.status = "Normal";
      eventBus.$emit("serverStatusReset", this.status);
    }
  },
  created() {
    eventBus.$on("serverDetails", data => {
      this.id = data.id;
      this.status = data.status;
    });
  }
};
</script>

<style>
</style>
