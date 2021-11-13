<template>
  <div class="task-tracker">
      <h1>Task Tracker</h1>
      <TasksFilter :filterText="filterText" @changeText="updateFilter" />
      <Tasks :tasks="filteredTasks" @deleteTask="deleteTask" @updateTask="updateTask"/>
  </div>
</template>

<script>
import Tasks from './tasks-tracker/Tasks.vue';
import TasksFilter from './tasks-tracker/TaskFilter.vue';

export default {
    name:"TaskTracker",
    data() {
        return{
            filterText: "",
            tasks: [],
            filteredTasks: []
        }
    },
    components: {
        Tasks,
        TasksFilter,
    },
    methods: {
        updateTask(id){
            this.tasks.map((task) => {
                if(task.id === id) task.done = !task.done
            })
        },
        deleteTask(id){
            this.tasks = this.tasks.filter((task) => {
                return task.id !== id
            })
            this.filterTasks(this.filterText);
        },
        updateFilter(value){
            this.filterText = value
        },
        filterTasks(text){
            this.filteredTasks = this.tasks.filter(function(task){
                return task.text.toLowerCase().includes(text.toLowerCase())
            })
        }
    },
    watch: {
        filterText: {
            handler(value){
                this.filterTasks(value)
            }
        }
    },
    created(){
        this.tasks = [
            {
                id: 1,
                text:"I will walk my dog...",
                done: false,
            },
            {
                id: 2,
                text:"Eat",
                done: true,
            },
            {
                id: 3,
                text:"Sleep",
                done: true,
            },
            {
                id: 4,
                text:"Repeat",
                done: false,
            },
        ];
        this.filteredTasks = this.tasks;
    },
    
}
</script>

<style scoped>
    .task-tracker{
        width: 100%;
        height: 500px;
    }
    h1{
        color: black;
    }
</style>