<template>
  <div id="todo">
    <div>
      {{ taskNo - 1 }}/5
      <b-button type="reset" variant="danger" v-on:click="() => onReset()">reset</b-button>
    </div>

    <div class="taskTable">
      <table class="my-2">
        <tr v-for="task in tasks" v-bind:key="task.id">
          <td>
            <input type="checkbox" v-model="task.done" />
          </td>
          <td>
            <p>
              {{ task.name }}
            </p>
          </td>
          
        </tr>
      </table>
    </div>

    <div class="creatNewTask mt-3">
      <b-container>
        <b-row class="justify-content-md-center">
          <b-col cols="8" class="ms-5 md-5 lg-5">
            <b-input type="text" class="inputTask" v-model="newTask" />
          </b-col>
        </b-row>

        <div class="mt-3">
          <b-button
            variant="outline-primary"
            type="button"
            v-on:click="onCreateNewTask"
          >
            Addtask
          </b-button>
          <b-button type="button" v-on:click="onCancel"> Cancel </b-button>
        </div>
      </b-container>
    </div>
  </div>
</template>
<script>
export default {
  name: "App",
  data() {
    return {
      newTask: "",
      tasks: [],

      checkNo: true,
      taskNo: 1,
    };
  },
  methods: {
    onCreateNewTask() {
      this.tasks = [
        {
          id: new Date().getTime(),
          name: this.newTask,
          done: false,
          taskNo: this.taskNo++,
        },
        ...this.tasks,
      ];
      this.newTask = "";
    },

    onReset() {
      this.tasks = [];
      this.taskNo = 1;
    },

    onCancel() {
      this.newTask = "";
    },
  },
};
</script>

<style>
#todo {
  margin-top: 30px;
  text-align: center;
}
.creatNewTask {
  margin-bottom: 10px;
}
.taskTable table {
  background-color: rgb(153, 153, 153);
  color: white;
  margin: 0px auto;
  width: 420px;
}
.taskTable p {
  text-align: left;
}
</style>