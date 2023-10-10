<script setup>
  import { reactive } from 'vue';
  import Cabecalho from './components/cabecalho.vue'
  import Formulario from './components/Formulario.vue'


  const estado = reactive({
    filtro: 'todas',
    tarefaTemp:'',
    tarefas:[
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
  });

  const getTarefasPendentes = () => {
    return estado.tarefas.filter(tarefa => !tarefa.finalizada)
  }

  const getTarefasFinalizadas = () => {
    return estado.tarefas.filter(tarefa => tarefa.finalizada)
  }

  const getTarefasFiltradas = () => {
    const { filtro } = estado;

    switch (filtro) {
      case 'pendentes':
        return getTarefasPendentes();
      case 'finalizadas':
        return getTarefasFinalizadas(); 
      default:
        return estado.tarefas;
  }
}

const cadastraTarefa = () => {
  const tarefaNova = {
    titulo: estado.tarefaTemp,
    finalizada: false,
  }
  estado.tarefas.push(tarefaNova);
  estado.tarefaTemp = '';
}

</script>

<template>
   <div class="container">
    

    <ul  class="list-group mt-4">
       <li class="list-group-item" v-for="tarefa in getTarefasFiltradas ()">
        <input @change="evento => tarefa.finalizada = evento.target.checked" :checked="tarefa.finalizada" :id="tarefa.titulo" type="checkbox">
        <label :class="{done:tarefa.finalizada ===true}" class="ms3" :for="tarefa.titulo">
          {{tarefa.titulo}}
        </label>
       </li>
    </ul>
   </div>
</template>

<style scoped>
  .done{
    text-decoration: line-through;
  }
</style>
