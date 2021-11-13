<template>
  <li class="task" v-bind:class="{done: task.done}" v-on:click.self="updateTask(task.id)">
      {{task.text}}
      <span class="delete" v-on:click="deleteTask(task.id)">X</span>
  </li>
</template>

<script>
export default {
    name: "Task",
    props: {
        task: Object
    },
    methods: {
        updateTask(id){
            this.$emit("updateTask", id)
        },
        deleteTask(id){
            this.$emit("deleteTask", id)
        }
    }
}
</script>

<style scoped>
    .task{
        min-width: 100px;
        width: auto;
        height: 100px;
        color: black;
        background-color: white;
        border: 1px solid black;
        box-shadow: -4px 4px 8px black;
        display: flex;
        justify-content: center;
        align-items:center;
        flex-direction: column;
        position: relative;
        margin:0 8px;
        padding: 8px;
        cursor: pointer;
        transition: all 0.2s ease-in;
        font-size: 24px;
    }
    .task .delete{
        position: absolute;
        top: 4px;
        right: 4px;
        color: rgba(0,0,0,0);
        transition: all 0.2s ease-in;
    }
    .task:hover{
        background-color: rgb(6, 190, 0);
        color: white;
    }
    .task:hover .delete{
        color: rgba(255,255,255,1)
    }
    .task .delete:hover{
        color: red;
    }

    .task.done{
        background-color: gray;
        box-shadow: 0 0 4px black;
    }
    .task.done:hover{
        background-color: rgb(51, 40, 40);
    }
</style>