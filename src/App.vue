<template>
  <div id="app" style="margin:0 auto;width:700px;">
    <h1>MY TODO LIST</h1>

      <form style="margin-bottom: 20px;" v-on:submit='addTask'>
        <input required="required" placeholder="Enter a task" style="float:right;width: 90%;height:40px;" type="text" v-model='tasks.name'><br/>
        <button style="margin-top:15px;margin-bottom:30px;float:right;background-color: green;color:#ffffff;padding:12px;cursor:pointer;" type="submit">Add Todo Task</button>
      </form><br/><br/>

<table class="table" border="1" style="text-align: left;float:right;">
  <thead>
  <th style="padding:7px;width:33%;">Select</th>
  <th style="padding:7px;width:34%;">Task Name</th>
  <th style="padding:7px;width:33%;">&nbsp;&nbsp;Delete</th>
  </thead>
  <tbody>
  <tr v-for='task in tasks'>
    <td><input type="checkbox" v-model="task.done"/></td>
    <td><span :class="{ taskDone: task.done }">{{ task.name }}</span></td>
    <td><button style="cursor:pointer;padding:6px;margin:10px;background-color: red;color:#ffffff;" v-on:click="deleteTask(task)">DELETE</button></td>
  </tr>
  </tbody>
</table>
  </div>
</template>

<script>
export default {
  name: 'app',
  data () {
    return {
        tasks:[
            {name: 'I will be in office on Monday', done:false},
            {name: 'Am Travelling Tonight', done:false},
            {name: 'I love Programming with Vue', done:false},
        ]
    }
  },
   methods:{
      addTask:function(e){
          e.preventDefault();
this.tasks.push({
    name:this.tasks.name,
    done: false
});
      },
       deleteTask:function (task) {
           this.tasks.splice(this.tasks.indexOf(task), 1)
       }
   }

}
</script>

<style lang="scss">
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}

h1, h2 {
  font-weight: normal;
}

ul {
  list-style-type: none;
  padding: 0;
}

li {
  display: inline-block;
  margin: 0 10px;
}

a {
  color: #42b983;
}
  .taskDone{
    text-decoration: line-through;
  }
</style>
