<template>
  <div class="col-xs-12 col-sm-6">
    <!-- TODO: @click send id and status to ServerDetails using event bus -->
    <ul class="list-group">
      <app-server
        v-for="server in servers"
        :key="server.id"
        :id="server.id"
        :status="server.status"
      ></app-server>
    </ul>
  </div>
</template>

<script>
import Server from "./Server.vue";

export default {
  data() {
    return {
      servers: [
        { id: 1, status: "Normal" },
        { id: 2, status: "Critical" },
        { id: 3, status: "Unknown" },
        { id: 4, status: "Normal" }
      ]
    };
  },
  components: {
    "app-server": Server
  }
};
</script>

<style>
</style>
