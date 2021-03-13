<template>
  <div class="home">

    <v-text-field
      v-model="newTask"
      class="ma-2"
      outlined
      label="Add  New Task"
      append-icon="mdi-plus"
      clearable
      hide-details
      @click:append="addTask"
    ></v-text-field>

    <div
      v-for="task in tasks"
      :key="task.id"
    >

        <v-list-item>

          <template v-slot:default="{ active }">
            <v-list-item-action>
              <v-checkbox :input-value="active"></v-checkbox>
            </v-list-item-action>

            <v-list-item-content>
              <v-list-item-title>{{ task.title }}</v-list-item-title>
            </v-list-item-content>
          
            <v-list-item-action>
              <v-btn
                icon
                @click.stop="deleteTask(task.id)"
              >
                <v-icon color="primary lighten-1">mdi-delete</v-icon>
              </v-btn>
            </v-list-item-action>
          </template>

        </v-list-item>

      <v-divider></v-divider>

    </div>

  </div>
    
</template>

<script>

export default {
  name: 'Home',
  data() {
    return {
      newTask: '',
      tasks: [
        {
          id: '1',
          title: 'Wakeup',
          done: false
        },
        {
          id: '2',
          title: 'Workout',
          done: false
        },
        {
          id: '3',
          title: 'Study',
          done: false
        }
      ]
    }
  },
  methods: {
    addTask(){
      let newTaskObj = {
        id: Date.now(),
        title: this.newTask,
        done: false
      }
      this.tasks.unshift(newTaskObj)
    } ,
    deleteTask(taskId) {
      this.tasks = this.tasks.filter(task => task.id != taskId)
    }
  }
}
</script>
