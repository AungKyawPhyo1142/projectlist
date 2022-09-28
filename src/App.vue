<template>
  <div class="">

    <h1 class="text-center bg-primary text-white p-3">{{name}}'s Todo List</h1>
    <div class="container">
      
      <div class="row bg-dark text-white border rounded mb-4">
        <div class="col fs-2">Tasks</div>
        <div class="col-2 fs-2">Done</div>
      </div>
    
      <div class="row fs-4 p-1 mb-1 bg-secondary border rounded text-white" v-for="(task,index) in filterTasks" v-bind:key="index">
        <div class="col" :class=" task.done ? 'delete':'' ">{{task.action}}</div>
        <div class="col-2"><input type="checkbox" class="" v-model="task.done"></div>
      </div>

      <div class="row mt-4 d-flex justify-content-between">
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
    tasks: [
      {'action': 'Buy new phone','done': false},
      {'action': 'Buy new shoe','done': true},
      {'action': 'Wash clothes','done': false},
      {'action': 'Wash Dishes','done': true}
    ]
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
    }
  }

}

</script>

<style>
  .delete{
    text-decoration: line-through;
  }
</style>