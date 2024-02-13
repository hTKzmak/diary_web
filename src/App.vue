<template>
  <div class="container">
    <InputForm @handle="addTask" />
    <TaskList :data="data" :deleteItem="deleteItem" :deleteDay="deleteDay" />
  </div>
</template>

<script>
import InputForm from './components/InputForm.vue'
import TaskList from './components/TaskList.vue'

export default {
  components: { InputForm, TaskList },
  data() {
    return {
      data: [

        {
          id: 1, dayName: 'ПН', tasks: [
            { id: 1, necessary: 'true', description: 'test' },
            { id: 2, necessary: 'false', description: 'test' },
            { id: 3, necessary: 'true', description: 'test' }
          ]
        }

      ]
    }
  },
  methods: {
    addTask(day, important, title) {
      let existedDay = this.data.find(elem => elem.dayName == day);

      let taskItem = {
        id: Date.now(),
        necessary: important,
        description: title
      }

      let newTask = {
        id: Date.now(),
        dayName: day,
        tasks: [
          taskItem
        ]
      }


      if (existedDay) {
        console.log(newTask)
        existedDay.tasks.push(taskItem)
      }
      else {
        console.log(newTask)
        this.data.push(newTask)
      }

    },

    deleteItem(taskID) {
      this.data.forEach(day => {
        day.tasks = day.tasks.filter(task => task.id !== taskID);
        if(day.tasks.length == 0){
          this.deleteDay(day.id)
        }
      });
    },

    deleteDay(dayId) {
      this.data = this.data.filter(day => day.id !== dayId);
    }

  }
}
</script>


<style></style>
