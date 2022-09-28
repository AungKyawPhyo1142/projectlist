<template>
  <div class="">

    <h1 class="text-center bg-primary text-white p-3">{{name}}'s Todo List</h1>
    <div class="container">
      
      <div class="row my-4">
        <div class="col-4">
          <input type="text" name="" v-on:keyup.enter="addItems()" id="" v-model="newTask" class="form-control">
        </div>
        <div class="col">
          <button class="btn btn-info" @click="addItems()">Add Task</button>
        </div>
      </div>

      <div class="row text-dark text-uppercase mb-4">
        <div class="col fs-2">Tasks</div>
        <div class="col-2 fs-2 text-end">Done</div>
      </div>

      <div class="" v-if="filterTasks.length!=0">      
        <div class="row mx-1 fs-4 p-1 mb-1 bg-secondary border rounded text-white" v-for="(task,index) in filterTasks" v-bind:key="index">
          <div class="col" :class=" task.done ? 'delete':'' ">{{task.action}}</div>
          <div class="col-2 text-end"><input type="checkbox" class="" v-model="task.done"></div>
        </div>
      </div>


      <div class="alert alert-warning text-dark" v-else>There are no tasks at the moment</div>

      <div class="row mx-1 mt-4 d-flex justify-content-between">
        <button class="col-3 btn btn-danger" v-bind="hideCompleted" @click="hideCompletedItems()">Hide Complete Tasks</button>
        <button class="col-3 btn btn-primary"  v-bind="hideCompleted" @click="showCompletedItems()">Show Complete Tasks</button>
      </div>

    </div>
  </div>
</template>

<script>

export default{
  
  name: "App", // name of the component
  
  data: ()=> ({
    name:'Sebastian',
    hideCompleted: false,
    newTask: '',
    tasks: []
  }),

  computed: {
  
    filterTasks(){
      return this.hideCompleted ? this.tasks.filter(item => !item.done) : this.tasks;      
    }

  },

  methods: {
    hideCompletedItems(){
      this.hideCompleted=true;
    },
    showCompletedItems(){
      this.hideCompleted=false;
    },
    addItems(){

      if(this.newTask === ''){
        return alert('Please add a task to add');
      }
      else {
        this.tasks.push({'action':this.newTask, 'done':false});
      }

      this.newTask = '';
    }
  }

}

</script>

<style>
  .delete{
    text-decoration: line-through 3px;
  }
</style>