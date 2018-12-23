<template>
  <li class="list-group-item" @click="serverDetails">Server #{{editId}} - Status: {{editStatus}}</li>
</template>

<script>
import { eventBus } from "../../main.js";

export default {
  data() {
    return {
      editId: this.id,
      editStatus: this.status
    };
  },
  props: {
    id: Number,
    status: String
  },
  methods: {
    serverDetails() {
      eventBus.$emit("serverDetails", {
        id: this.editId,
        status: this.editStatus
      });
    }
  },
  created() {
    eventBus.$on("serverStatusReset", data => {
      console.log(data);
      this.editStatus = data;
    });
  }
};
</script>
