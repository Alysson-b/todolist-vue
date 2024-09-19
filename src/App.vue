
<template>
 <div id="app">
    <h1>To Do List</h1>

    <input v-model="newTask" @keyup.enter="addTask" placeholder="Adicionar nova tarefa" />
    <ul>
        <li v-for="(task, index) in tasks" :key="index">
          <span :class="{ completed: task.completed }" @click="toggleTask(index)">
          {{task.text}}
          </span>
          <button @click="removeTask(index)">Remover</button>
        </li>
      </ul>
  </div>
</template>

<script>
export default {
  data() {
    return {
      newTask: '',
      tasks: []
    };
},
methods: {
    addTask() {
        if(this.newTask.trim()){
        this.tasks.push({ text: this.newTask, completed: false })
        this.newTask = '';
  }
},
removeTask(index){
  this.tasks.splice(index, 1)
},

toggleTask(index){
  this.tasks[index].completed = !this.tasks[index].completed
    },
  }
};
</script>

<style>

body{
  height: 100vh;
  margin: 0;
  display: flex;
  justify-content: center;
  align-items: center;
  background-color: #87CEFA;
}

#app{
  display: flex;
  align-items: center;
  font-family: 'poppins', sans-serif;
  flex-direction: column;
  width: 400px;
  margin: 0 auto;
  padding: 20px;
  background-color: #f9f9f9;
  box-shadow: 0 4px 8px rgba(0, 0, 0, 0.3);
  border-radius: 8px;
  max-width: 100%;
}
h1{
  color: #ff6347;
  text-align: center;
  font-size: 3rem;
  margin-bottom: 20px;
}
input{
  width: 100%;
  padding: 10px;
  font-size: 1rem;
  border: 2px solid #ff6347;
  border-radius: 12px;
  margin-bottom: 20px;
  outline: none;
  transition: border-color 0.3s;
  
}
input:focus{
    border-color: #32cd32;
}
ul{
  list-style-type: none;
  padding: 0;
  cursor: pointer;
}
li{
  background-color: #fff;
  gap: 12px;
  padding: 10px 25px;
  margin-bottom: 10px;
  display:flex;
  justify-content: space-between;
  align-items: center;
  border-radius: 8px;
  box-shadow: 0 2px 4px rgba(0, 0, 0, 0.1);
  transition: background-color 0.3s;

}
li:hover{
background-color: #f1f1f1;
}

.completed{
    text-decoration: line-through;
    color: gray;
}

button {
  background-color: #ff6347;
  color: white;
  border: none;
  border-radius: 4px;
  padding: 5px 10px;
  cursor: pointer;
  font-size: 0.9rem;
  transition: background-color 0.3s;
}
button:hover{
  background-color: #e5533b;
}
</style>
