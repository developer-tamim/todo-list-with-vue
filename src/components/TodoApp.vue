<template lang="">
  <div class="container" style="max-width: 600px">
    <div>
      <!-- heading -->
      <h1 class="text-center mt-5">Todo List in Vue</h1>
      <!-- input -->
      <div class="d-flex mt-5">
        <input
          type="text"
          v-model="task"
          placeholder="Enter your task"
          class="w-100 form-control"
        />
      </div>

      <!-- table -->
      <div class="mt-3">
        <table class="table table-bordered">
          <thead>
            <tr>
              <th scope="col">Tasks</th>
              <th scope="col" style="width:100px;">Status</th>
              <th scope="col" class="text-center">Edit</th>
              <th scope="col" class="text-center">Delete</th>
            </tr>
          </thead>
          <tbody>
            <tr>
              <th scope="row">1</th>
              <td>Mark</td>
              <td>Otto</td>
              <td>@mdo</td>
            </tr>  
          </tbody>
        </table>
      </div>
    </div>
  </div>
</template>

<script>
    export default {
        name: "TodoApp",
    };
</script>

<style lang=""></style>
