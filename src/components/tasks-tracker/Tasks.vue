<template>
      <ul class="tasks">
          <Task v-for="task in tasks" v-bind:key="task.id" v-bind:task="task"
            v-on:deleteTask="deleteTask" v-on:updateTask="updateTask"/>
      </ul>
</template>

<script>
import Task from './Task.vue';

export default {
    name: "Tasks",
    props: {
        tasks: Array
    },
    components: {
        Task
    },
    methods: {
        updateTask(id){
            this.$emit('updateTask', id)
        },
        deleteTask(id){
            this.$emit('deleteTask', id)
        }
    }
}
</script>

<style scoped>
    ul{
        list-style-type: none;
        padding: 8px;
        display: flex;
        flex-direction: row;
        flex-wrap: wrap;
        width: auto;
    }
   
</style>