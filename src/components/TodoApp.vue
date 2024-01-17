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
        <button class="btn btn-warning rounded-0" @click="submitTasks">Submit</button>
      </div>

      <!-- table -->
      <div class="mt-3">
        <table class="table table-bordered">
          <thead>
            <tr>
              <th scope="col">Tasks</th>
              <th scope="col" style="width: 100px">Status</th>
              <th scope="col" class="text-center">Edit</th>
              <th scope="col" class="text-center">Delete</th>
            </tr>
          </thead>
          <tbody>
            <tr v-for="(task, index) in tasks" :key="index">
              <td>{{ task.task }}</td>
              <td>
                <span
                  class="pointer select"
                  @click="changeStatus(index)"
                  :class="{
                    'text-danger': task.status === 'to-do',
                    'text-success': task.status === 'in-progress',
                    'text-warning': task.status === 'finished',
                  }"
                >
                {{ capitalizeFirstChart(task.status) }}
                </span>
              </td>
              <td class="text-center">
                <div @click="editTasks(index)">
                  <i class="fa-regular fa-pen-to-square"></i>
                </div>
              </td>
              <td class="text-center">
                <div @click="deleteTasks(index)">
                  <i class="fa-solid fa-trash"></i>
                </div>
              </td>
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
  props: {
    msg: String,
  },
  data() {
    return {
      task: "",
      editTask: null,
      status: ["to-do", "in-progress", "finished"],
      tasks: [
        {
          task: "Tasks1",
          status: "to-do",
        },
        {
          task: "Tasks2",
          status: "in-progress",
        },
        {
          task: "Tasks3",
          status: "finished",
        },
      ],
    };
  },
  methods: {
    capitalizeFirstChart(srt) {
      return srt.charAt(0).toUpperCase() + srt.slice(1);
    },
    changeStatus(index) {
      let newIndex = this.status.indexOf(this.tasks[index].status);
      if (++newIndex > 2) newIndex = 0;
      this.tasks[index].status = this.status[newIndex];
    },
    editTasks(index) {
      this.task = this.tasks[index].task;
      this.editTask = index;
    },
    deleteTasks(index) {
      this.tasks.splice(index, 1);
    },
    submitTasks() {
      if (this.task.length === 0) return;
      if (this.editTask != null) {
        this.tasks[this.editTask].task = this.task;
        this.editTask = null;
      } else {
        this.tasks.push({
          task: this.task,
          status: "to-do",
        });
      }
      this.task = "";
    },
  },
};
</script>

<style lang=""></style>
