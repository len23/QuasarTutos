<template>
  <q-page padding>
      <ul>
        <task v-for="(task,index) in tasks"
        :key="task.id" 
        :task="task" 
        :index="index"
        ></task>
      </ul>
  </q-page>
</template>

<script>
export default {
   data() {
     return {
       tasks: [
         {
           id:1,
           name: 'Watch Udemy',
          dueDate: '2021/06/12',
          dueTime: '19:08'
         },
          {
            id:2,
            name: 'Play Ps5',
          dueDate: '2021/06/12',
          dueTime: '18:08'
         },
         {
           id:3,
           name: 'Wash the dishes',
          dueDate: '2021/06/12',
          dueTime: '20:08'
         }
       ]
     }
  },
  components: {
    'task' : require('../components/Task').default
  }
}
</script>

<style>

</style>
