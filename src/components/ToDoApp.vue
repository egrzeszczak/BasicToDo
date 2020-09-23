<template>
  <div class="app">
    <div class="title">
        <img src="../assets/clipboard.svg"><br/>
        
    </div>
    <div class="task-input">
      <form v-on:submit.prevent="noop">
        <input 
        type="text" 
        placeholder="Add a new task..." 
        v-model="newTask" 
        ref="task-input-ref"
        />
        <button @click="addTask">+</button>
      </form>
    </div>
    <div class="items">
      <span v-if="items.length === 0">You got to start somewhere.</span>
      <ToDoItem
        v-for="item in items"
        :key="item.id"
        :item="item"
        @finishTask="completeTask"
      ></ToDoItem>
    </div>
  </div>
</template>

<script>
import ToDoItem from "./ToDoItem.vue"
export default {
  components: {
    ToDoItem: ToDoItem
  },
  data() {
    return {
      newTask: "",
      newId: 1,
      items: [ /* Tutaj będą taski */ ],
    };
  },
  methods: {
    addTask() {
      this.items.push({
        id: this.newId,
        title: this.newTask,
        completed: false,
      });
      this.newId++;
      this.newTask = '';
    },
    completeTask(taskId) {
      const index = this.items.findIndex(el => el.id === taskId); 
      this.items[index].completed = true;
    }
  },
};
</script>

<style lang="scss">
   body, html{
      margin: 0;
      padding: 0;
    } 
  .app{
    background: #31323b;
    color: white;
    padding: 2rem 0;
    min-height: calc(100vh - 4rem);
    font-family: 'Arial';
    button{
      background: inherit;
      border-radius: 0;
      border: none;
      color: white;
      width: 52px;
      height: 52px;
      transition: .15s all cubic-bezier(.65,.05,.36,1);
      &:hover{
        cursor: pointer;
        background: gainsboro;
        color: black;
      }
    }
    .title{
      text-align: center;
      margin-bottom: 1rem;
      img{
          color: white;
          height: 64px;
          width: auto;
      }

    }
    .task-input{
      display: flex;
      justify-content: center;
      button{
        border: 1px solid gainsboro;
      }
      input{
        background: inherit;
        border: 0;
        border-bottom: 1px solid gainsboro;
        color: white;
        padding: 1rem;
        width: 200px;
        margin-right: 1rem;
        transition: .15s all cubic-bezier(.65,.05,.36,1);
        transition-delay: .1s;
        &:focus{
          width: 400px;
          background: gainsboro;
          color: #222222;
        }
      }
    }
    .items{
      padding: 2rem 20%;
      text-align: center;
      span{
        color: gainsboro;
        font-size: 12px;
      }
    }
  }
</style>
