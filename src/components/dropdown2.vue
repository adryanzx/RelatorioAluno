<template>
  <div class="is-flex --is-flex-wrap">
    <div class="field mr-4"> 
    <label class="label" for="selecionarTipo">Selecionar tipo:</label> 
    <div class="control"> 
      <div class="select"> 
    <select id="selecionarTipo" v-model="tipoSelecionado" style="min-width: 300px"> 
      <option value="prova">Prova</option>
      <option value="aula">Aula</option>
    </select>
    </div>
    </div>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      tipoSelecionado: null
    };
  }
};
</script>
