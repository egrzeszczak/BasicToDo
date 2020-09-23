<template>
  <div>
    <ToDoApp></ToDoApp>
  </div>

</template>

<script>
import myToDoApp from './components/ToDoApp.vue'
export default{
  components: {
    ToDoApp: myToDoApp,
  }
}
</script>