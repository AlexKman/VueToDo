<template>
  <div class="container">
    <h1 class="text-center mt-8">My app</h1>
    <div class="d-flex">
      <input type="text" placeholder="Enter Task" class="form-control" />
      <button class="btn btn-warning rounded-0">Submit</button>
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
        <tr>
          <th>Play Games</th>
          <td>To do</td>
          <td>
            <div class="text-center">
              <span class="fa fa-pen"></span>
            </div>
          </td>
          <td>
            <div class="text-center">
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
  name: "HelloWorld",
  props: {
    msg: String,
  },
  data() {
    return {
      tasks: [
        { name: "Make Pasta", status: "To do" },
        { name: "Eat Pasta", status: "To do" },
      ],
    };
  },
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped></style>
