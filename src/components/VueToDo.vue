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
          <td>{{ task.status }}</td>
          <td>
            <div class="text-center" @click="editTask(index)">
              <span class="fa fa-pen"></span>
            </div>
          </td>
          <td>
            <div class="text-center" @click="deleteTask(index)">
              <span class="fa fa-trash"></span>
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
      tasks: [
        { name: "Make Pasta", status: "To do" },
        { name: "Eat Pasta", status: "To do" },
      ],
    };
  },

  methods: {
    addTask() {
      if (this.task.length === 0) return;

      this.tasks.push({ name: this.task, status: "To do" });

      this.task = "";
    },

    deleteTask(index) {
      this.tasks.splice(index, 1);
    },

    editTask(index) {
      console.log(index);
    },
  },
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped></style>
