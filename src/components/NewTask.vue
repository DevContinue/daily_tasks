<template>
  <input
    type="text"
    class="form-control"
    placeholder="Neue Aufgabe"
    v-model="content"
  />
  <div class="d-grid my-2">
    <button class="btn btn-secondary" @click="submitTask()">Eintragen</button>
  </div>
</template>

<script>
export default {
  name: "NewTask", 
  emits: {
    "new-task": (task) => {
      if (task.content === "") {
        console.warn("NewTaskComponent: Der Conent sollte nicht leer sein.");
        return false;
      }
      return true;
    },
  },
  data() {
    return {
      content: "",
    };
  },
  computed: {
    maxNumbers() {
      return this.maxNumberOfChars - this.content.length;
    }
  },
  methods: {
    submitTask() {
      this.$emit("new-task", {
        // Payload
        content: this.content,
      });
      this.content = "";
    },
  },
};
</script>

<style lang="scss" scoped></style>
