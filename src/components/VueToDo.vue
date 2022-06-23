<template>
  <div class="container">
    <h1 class="text-center mt-8">My app</h1>
    <div class="d-flex">
      <input type="text" placeholder="Enter Task" class="form-control" />
      <button class="btn btn-warning rounded-0">Submit</button>
    </div>
  </div>
</template>

<script>
export default {
  name: "HelloWorld",
  props: {
    msg: String,
  },
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped></style>
