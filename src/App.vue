<template>
  <div class="container mt-5">
    <div class="row">
      <div class="col-4" v-for="statusCard in statusCards" :key="statusCard.status">
        <StatusCard 
          :title="statusCard.title"
          :titleClasses="statusCard.titleClasses"
          :status="statusCard.status"
          :newTasks="statusCard.newTasks"
          :tasks="filteredTasks(statusCard.status)"
          @new-task="addTask"
        />
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
          status: 1,
        },
        {
          id: 3,
          content: "Vue.js Üben, Üben, Üben.",
          status: 2,
        },
      ],
      statusCards: [
        {
          title: "Neu Aufgabe",
          titleClasses: "bg-secondary text-white",
          newTasks: true,
          status: 0,
        },
        {
          title: "In Bearbeitung",
          titleClasses: "bg-primary text-white",
          newTasks: false,
          status: 1,
        },
        {
          title: "Erledigt",
          titleClasses: "bg-success text-white",
          newTasks: false,
          status: 2,
        },
      ],
    };
  },
  methods: {
    filteredTasks(status) {
      return this.tasks.filter((task) => task.status === status);
    },
    addTask (task) {
      task.id = Math.random();
      this.tasks.push(task);
    }
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
  font-size: 20px;

  display: flex;
  justify-content: center;
}

* {
  box-sizing: border-box;
  margin: 0;
  padding: 0;
}

.card {
  min-width: 15rem;
}
</style>
