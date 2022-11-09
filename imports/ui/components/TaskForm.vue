<template>
  <form
    className="new-task"
    @submit.prevent="handleSubmit"
    class="new-task task-form"
  >
    <input type="text" placeholder="Type to add new tasks" v-model="newTask" />
    <button type="submit">Add Task</button>
  </form>
</template>

<script>
export default {
  data() {
    return {
      newTask: "",
    };
  },
  methods: {
    handleSubmit(event) {
      if (this.newTask.length === 0) return;

      Meteor.call("tasks.insert", this.newTask.trim());

      // Clear form
      this.newTask = "";
    },
  },
};
</script>
