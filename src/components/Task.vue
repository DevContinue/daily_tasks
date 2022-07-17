<template>
  <div class="alert" :class="alertClass">{{ task.content }}</div>
</template>

<script>
export default {
  name: "Task",
  props: {
    task: Object,
    alertColor: String,
  },
  computed: {
    alertClass() {
      return `alert-${this.alertColor}`
    }
  }
};

</script>

<style lang="scss" scoped></style>
