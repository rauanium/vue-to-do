<template>
  <div class="to-do">
    <input class="input" type="text" placeholder="Enter task" v-model = "singleTask">
    <a class="button is-primary is-fullwidth" @click="addTask">Add task</a>
    <p @click = "statusSort" class="button is-primary is-fullwidth">Sort tasks by Pending</p>
    <p class = "inlinePar">Completed: {{ completedTasks }}</p>
    <p class = "inlinePar">Pending: {{ pendingTasks }}</p>

    <div  v-for = "(task, index) in tasks" :class="{pending:pending, completed: task.status}" ref = "taskDiv" >
      <p id = "title">{{ task.title }}</p>
      <span @click = "editTask(index)" ><i class="far fa-edit" ></i></span>
      <span @click = "delteTask(index)" ><i class="far fa-trash-alt" ></i></span>
      <span @click = "doneTask(index)"><i class="far fa-check-circle"></i></span>

    </div>
  </div>
</template>

<script>
export default {
  name: 'TaskComp',
  data(){
    return {
      tasks: [{
        title: "wash dishes",
        status: 0
      }, {
        title: "math exam preperation",
        status: 0
      }],

      singleTask: "",
      pending: true
      

    }
  },

  methods:{
    addTask(){
      this.tasks.unshift({title: this.singleTask, status: 0})
      this.singleTask = ""


    },
    delteTask(index){
      this.$delete(this.tasks, index)
    },

    doneTask(index){
    this.tasks[index].status = 1 
      
    },
    editTask(index){
      this.singleTask = this.tasks[index].title
      this.delteTask(index)
    },
    statusSort(){
      for(var i in this.tasks){
        if(this.tasks[i].status == 1){
          this.tasks.push({title: this.tasks[i].title, status: this.tasks[i].status})
          this.$delete(this.tasks, i)
        }
      }




    }

    
  },
  computed:{
    completedTasks(){
      var counter = 0
      for(var index in this.tasks){
        if(this.tasks[index].status == 1){
          counter += 1
        }
      }
      return counter
    },
    pendingTasks(){
      var counter = 0
      for(var index in this.tasks){
        if(this.tasks[index].status == 0){
          counter += 1
        }
      }
      return counter

    },


  }
  
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
.to-do{
  width: 500px;
  margin: 0px auto;
}
.input{
  margin-bottom: 10px;
}
.button{
  margin-bottom: 10px;
}

.pending{
  background-color: #ff5959;
  margin-bottom: 5px;
  height: 100px;
}
.completed{
  background-color: #1abb9c;
  margin-bottom: 5px;
  height: 100px;
}
#title{ 
  font-size: 25px;
  padding: 15px 0px;
  font-weight: bold;
}
.inlinePar{
  display: inline;
  padding: 20px;
}

i{
  margin-right: 10px;
  font-size: 20px;
  padding-bottom: 10px;
}
</style>
