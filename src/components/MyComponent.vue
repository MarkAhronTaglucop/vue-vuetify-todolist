<template>
  <div class="home">
    <v-text-field
    v-model="newTaskTitle"
    @click:append="addTask"
    @keyup.enter="addTask"
      class="pa-3"
      append-inner-icon="mdi-plus"
      label="Add Task"
      variant="solo"
      hide-details
      clearable
    ></v-text-field>
    <v-list class="pt-0" select-strategy="classic">
      <div v-for="task in tasks" :key="task.id">
        <v-list-item
          :class="{ 'blue-lighten-5': task.done }"
          @click="doneTask(task.id)"
        >
          <template v-slot:prepend>
            <v-list-item-action start>
              <v-checkbox-btn
                v-model="task.done"
                @change="doneTask(task.id)"
              ></v-checkbox-btn>
            </v-list-item-action>
          </template>
          <template v-slot:append>
            <v-btn
              @click.stop="deleteTask(task.id)"
              color="primary"
              icon="mdi-delete"
              variant="text"
            ></v-btn>
          </template>

          <v-list-item-title
            :class="{ 'text-decoration-line-through': task.done }"
            >{{ task.title }}</v-list-item-title
          >
        </v-list-item>
        <v-divider></v-divider>
      </div>
    </v-list>
  </div>
</template>

<script>
export default {
  data() {
    return {
        newTaskTitle: '',
      tasks: [
        {
          id: 1,
          title: "Read a Book",
          done: false,
        },
        {
          id: 2,
          title: "Workout",
          done: false,
        },
        {
          id: 3,
          title: "Declutter",
          done: false,
        },
      ],
    };
  },
  methods: {
    addTask(){
        let newTask = {
            id: Date.now(),
            title: this.newTaskTitle,
            done: false
        }
        this.tasks.push(newTask)
        this.newTaskTitle=''
    },
    doneTask(id) {
      console.log(
        "Task ID:",
        id,
        "is now",
        this.tasks.find((task) => task.id === id).done
      );
    },
    deleteTask(id) {
      this.tasks = this.tasks.filter((task) => task.id !== id);
    },
  },
};
</script>




<style>
.blue-lighten-5 {
  background-color: #e3f2fd;
}
</style>