<template>
  <div class="container mt-5">
    <div class="row">
      <div class="col-4" v-for="i in 3" :key="i">
        <StatusCard />
      </div>
    </div>
  </div>
</template>

<script>
import StatusCard from "@/components/StatusCard.vue";

export default {
  name: "App",
  components: {
    StatusCard,
  },
  data() {
    return {
      tasks: [
        {
          id: 1,
          content: "Dashboard überarbeiten.",
          status: 0,
        },
        {
          id: 2,
          content: "Anwendung auf Vue.js umstellen.",
          status: 0,
        },
      ],
    };
  },
  methods: {
    newTasks() {
      return this.tasks.filter((task) => task.status === 0);
    },
  },
};
</script>

<style lang="scss">
@import "../node_modules/bootstrap/dist/css/bootstrap.min.css";

html,
body {
  width: 100%;
  height: 100%;
  background-color: $prime;
  color: $text;
  font-size: 20px;

  display: flex;
  justify-content: center;
}

* {
  box-sizing: border-box;
  margin: 0;
  padding: 0;
}
</style>
