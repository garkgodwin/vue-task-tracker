<template>
  <div class="tasks-filter">
      <input type="text" :value="filterText" @input="changeText($event.target.value)">
  </div>
</template>

<script>
export default {
    name:"TaskFilter",
    props: {
        filterText: String
    },
    methods: {
        changeText(value){
            this.$emit('changeText', value)
        }
    }

}
</script>

<style>

</style>