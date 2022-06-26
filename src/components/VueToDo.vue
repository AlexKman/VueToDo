<template>
  <div class="container">
    <h1 class="text-center mt-8">My app</h1>
    <div class="d-flex">
      <input
        v-model="task"
        type="text"
        placeholder="Enter Task"
        class="form-control"
      />
      <button @click="addTask" class="btn btn-warning rounded-0">Submit</button>
    </div>

    <table class="table table-bordered mt-4">
      <thead>
        <tr>
          <th scope="col">Task</th>
          <th scope="col">Status</th>
          <th scope="col" class="text-center">#</th>
          <th scope="col" class="text-center">#</th>
        </tr>
      </thead>
      <tbody>
        <tr v-for="(task, index) in tasks" :key="index">
          <th>{{ task.name }}</th>
          <td class="status-column">
            <span @click="changeStatus(index)">{{ task.status }}</span>
          </td>
          <td>
            <div class="text-center" @click="editTask(index)">
              <span class="fa fa-pen pointer"></span>
            </div>
          </td>
          <td>
            <div class="text-center" @click="deleteTask(index)">
              <span class="fa fa-trash pointer"></span>
            </div>
          </td>
        </tr>
      </tbody>
    </table>
  </div>
</template>

<script>
export default {
  name: "VueToDo",
  props: {
    msg: String,
  },
  data() {
    return {
      task: "",
      editedTask: null,
      statuses: ["To do", "In progress", "Complete"],
      tasks: [
        { name: "Make Pasta", status: "Complete" },
        { name: "Eat Pasta", status: "To do" },
      ],
    };
  },

  methods: {
    addTask() {
      if (this.task.length === 0) return;

      if (this.editedTask === null) {
        this.tasks.push({ name: this.task, status: "To do" });
      } else {
        this.tasks[this.editedTask].name = this.task;
        this.editedTask = null;
      }
      this.task = "";
    },

    deleteTask(index) {
      this.tasks.splice(index, 1);
    },

    editTask(index) {
      this.task = this.tasks[index].name;
      this.editedTask = index;
    },

    changeStatus(index) {
      let newIndex = this.statuses.indexOf(this.tasks[index].status);
      if (++newIndex > 2) newIndex = 0;
      this.tasks[index].status = this.statuses[newIndex];
    },
  },
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
.pointer {
  cursor: pointer;
}
.status-column {
  width: 140px;
}
</style>
