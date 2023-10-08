<script setup>
  import { reactive } from 'vue';

  const estado = reactive({
    tarefas: [
       {
         titulo: 'Estudar ES6',
         finalizada: false,
       },
       {
         titulo: 'Estudar SASS',
         finalizada: false,
       },
       {
         titulo: 'Ir para academia',
         finalizada: true,
       }
     ]
  })
</script>

<template>
   <div class="container">
    <header class="p-5 mb-4 bg-light rounded-3">
      <h1>Minhas tarefas</h1>
      <p>
       Voce possui 7 tarefas perndentes
      </p>
    </header>
    <form>
      <div class="row">
        <div class="col">
          <input type="text" placeholder="Digite aqui a descrição da tarefa" class="form-control">
        </div>
        <div class="col-md-2">
          <button type="submit" class="btn btn-primary">  cadastrar nova tarefa</button>
        </div>
        <div class="col-md-2">
          <select class="form-control">
            <option value="todas">Todas tarefas</option>
            <option value="pendentes">Pendentes</option>
            <option value="finalizadas">Finalizadas</option>
          </select>
        </div>
      </div>
    </form>
    <ul  class="list-group mt-4">
       <li class="list-group-item">
        <input type="checkbox">
        <label class="ms3" for="">
          Estudar ES6
        </label>
       </li>
    </ul>
   </div>
</template>

<style scoped>

</style>
