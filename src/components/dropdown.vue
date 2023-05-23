<template> 

    <div class="is-flex --is-flex-wrap"> 
  
      <!-- Select do periodo --> 
  
      <div class="field mr-4"> 
  
        <label class="label" :for="id">Período:</label> 
  
        <div class="control"> 
  
          <div class="select"> 
  
            <select :id="id" v-model="dadosPeriodo.periodoSelecionado" v-on:change="CarregaPeriodo()" style="min-width: 300px"> 
  
              <option v-for="periodo in itemsPeriodo" :key="periodo" :value="periodo"> 
  
                {{ periodo }} 
  
              </option> 
  
            </select> 
  
          </div> 
  
        </div> 
  
      </div> 
  
   
  
      <!-- Periodo personalizado --> 
  
      <div class="is-flex --is-flex-wrap" v-if="dadosPeriodo.periodoSelecionado == 'Personalizado'"> 
  
        <!-- Periodo inicio --> 
  
        <div class="field mr-3"> 
  
          <div class="control"> 
  
            <label class="label" for="custom-dt-inicio">Início:</label> 
  
            <input 
  
              min="2020-01-01" 
  
              v-bind:max="new Date().toISOString().slice(0, 10)" 
  
              class="input" 
  
              id="custom-dt-inicio" 
  
              v-model="dadosPeriodo.dataInicio" 
  
              type="date" 
  
              required="required" 
  
            /> 
  
          </div> 
  
          <label v-if="dataFinalMenorInicial" class="has-text-warning-dark is-size-7"> Data final menor que inicial. </label> 
  
        </div> 
  
   
  
        <!-- Periodo fim --> 
  
        <div class="field"> 
  
          <div class="control"> 
  
            <label class="label" for="custom-dt-fim">Fim:</label> 
  
            <input 
  
              v-bind:max="new Date().toISOString().slice(0, 10)" 
  
              class="input" 
  
              id="custom-dt-fim" 
  
              v-model="dadosPeriodo.dataFim" 
  
              type="date" 
  
              required="required" 
  
            /> 
  
          </div> 
  
          <label v-if="dataFinalMaiorAtual" class="has-text-warning-dark is-size-7"> Data final maior que atual. </label> 
  
        </div> 
  
   
  
        <!-- Botao buscar --> 
  
        <div> 
  
          <!-- Criar um espacamento no topo --> 
  
          <p class="mb-2">&nbsp;</p> 
  
          <button 
  
            class="button is-link is-outlined ml-4" 
  
            v-on:click="enviaComponentePai(true)" 
  
            :disabled="dataFinalMenorInicial || dataFinalMaiorAtual" 
  
          > 
  
            <span class="icon is-small"> 
  
              <i class="fas fa-search"></i> 
  
            </span> 
  
            <span>Buscar</span> 
  
          </button> 
  
        </div> 
  
      </div> 

      <!-- AÇÕES -->

      <div class="field mr-4"> 
  
  <label class="label" :for="id">Ações:</label> 

  <div class="control"> 

    <div class="select"> 

      <select :id="id" v-model="dadosações" v-on:change="Carregaações()" style="min-width: 300px"> 

        <option v-for="ações in itemsações" :key="ações" :value="ações"> 

          {{ ações }} 

        </option> 

      </select> 

    </div> 

  </div> 

</div> 



<!-- AÇÕES Ppersonalizado --> 

<div class="is-flex --is-flex-wrap" v-if="dadosações == 'Personalizado'"> 

  <!-- AÇÕES inicio --> 

  <div class="field mr-3"> 

    <div class="control"> 

      <label class="label" for="custom-dt-inicio">Início:</label> 

      <input 

        min="2020-01-01" 

        v-bind:max="new Date().toISOString().slice(0, 10)" 

        class="input" 

        id="custom-dt-inicio" 

        v-model="dadosações.dataInicio" 

        type="date" 

        required="required" 

      /> 

      

    </div> 

    <label v-if="dataFinalMenorInicial" class="has-text-warning-dark is-size-7"> Data final menor que inicial. </label> 

  </div> 



  <!-- Ações fim --> 

  <div class="field"> 

    <div class="control"> 

      <label class="label" for="custom-dt-fim">Fim:</label> 

      <input 

        v-bind:max="new Date().toISOString().slice(0, 10)" 

        class="input" 

        id="custom-dt-fim" 

        v-model="dadosações.dataFim" 

        type="date" 

        required="required" 

      /> 

    </div> 

    <label v-if="dataFinalMaiorAtual" class="has-text-warning-dark is-size-7"> Data final maior que atual. </label> 

  </div> 



  <!-- Botao buscar --> 

  <div> 

    <!-- Criar um espacamento no topo --> 

    <p class="mb-2">&nbsp;</p> 

    <button 

      class="button is-link is-outlined ml-4" 

      v-on:click="enviaComponentePai(true)" 

      :disabled="dataFinalMenorInicial || dataFinalMaiorAtual" 

    > 

      <span class="icon is-small"> 

        <i class="fas fa-search"></i> 

      </span> 

      <span>Buscar</span> 

    </button> 

  </div> 

</div> 


  
    </div> 
  
  </template> 
  
   
  
  <script> 
  
  export default { 
  
    data() { 
  
      return { 
  
        itemsPeriodo: [ 
  
          "Últimos 7 dias", 
  
          "Últimos 14 dias", 
  
          "Últimos 28 dias", 
  
          "Últimos 30 dias", 
  
          "Hoje", 
  
          "Ontem", 
  
          "Essa semana (dom)", 
  
          "Essa semana (seg)", 
  
          "Semana passada (dom)", 
  
          "Semana passada (seg)", 
  
          "Este mês", 
  
          "Mês passado", 
  
          "Este ano", 
  
          "Ano passado", 
  
          "Personalizado", 
  
        ], 
  
        dadosPeriodo: { 
  
          dataInicio: "", 
  
          dataFim: "", 
  
          periodoSelecionado: this.periodoPreSelecionado, 
  
        }, 
  
        dataFinalMenorInicial: false, 
  
        dataFinalMaiorAtual: false, 
  
      }; 
  
    }, 
  
   
  
    computed: { 
  
      id() { 
  
        return `input-${Math.random().toString(36).substring(2, 16) + Math.random().toString(36).substring(2, 16)}`; 
  
      }, 
  
    }, 
  
   
  
    props: { 
  
      periodoPreSelecionado: { 
  
        type: String, 
  
        default: "Este ano", 
  
      }, 
  
    }, 
  
   
  
    watch: { 
  
      dadosPeriodo: { 
  
        handler() { 
  
          this.validaData(); 
  
        }, 
  
        deep: true, 
  
      }, 
  
    }, 
  
   
  
    mounted() { 
  
      this.CarregaPeriodo(); 
  
    }, 
  
   
  
    methods: { 
  
      CarregaPeriodo() { 
  
        if (this.dadosPeriodo.periodoSelecionado == "Últimos 7 dias") { 
  
          //Últimos 7 dias 
  
          this.dadosPeriodo.dataInicio = new Date(new Date().setDate(new Date().getDate() - 7)).toISOString().substr(0, 10); 
  
          this.dadosPeriodo.dataFim = new Date().toISOString().substr(0, 10); 
  
        } else if (this.dadosPeriodo.periodoSelecionado == "Últimos 14 dias") { 
  
          //Últimos 14 dias 
  
          this.dadosPeriodo.dataInicio = new Date(new Date().setDate(new Date().getDate() - 14)).toISOString().substr(0, 10); 
  
          this.dadosPeriodo.dataFim = new Date().toISOString().substr(0, 10); 
  
        } else if (this.dadosPeriodo.periodoSelecionado == "Últimos 28 dias") { 
  
          //Últimos 28 dias 
  
          this.dadosPeriodo.dataInicio = new Date(new Date().setDate(new Date().getDate() - 28)).toISOString().substr(0, 10); 
  
          this.dadosPeriodo.dataFim = new Date().toISOString().substr(0, 10); 
  
        } else if (this.dadosPeriodo.periodoSelecionado == "Últimos 30 dias") { 
  
          //Últimos 30 dias 
  
          this.dadosPeriodo.dataInicio = new Date(new Date().setDate(new Date().getDate() - 30)).toISOString().substr(0, 10); 
  
          this.dadosPeriodo.dataFim = new Date().toISOString().substr(0, 10); 
  
        } else if (this.dadosPeriodo.periodoSelecionado == "Hoje") { 
  
          //Hoje 
  
          this.dadosPeriodo.dataInicio = new Date().toISOString().substr(0, 10); 
  
          this.dadosPeriodo.dataFim = new Date().toISOString().substr(0, 10); 
  
        } else if (this.dadosPeriodo.periodoSelecionado == "Ontem") { 
  
          //Ontem 
  
          this.dadosPeriodo.dataInicio = new Date(new Date().setDate(new Date().getDate() - 1)).toISOString().substr(0, 10); 
  
          this.dadosPeriodo.dataFim = new Date().toISOString().substr(0, 10); 
  
        } else if (this.dadosPeriodo.periodoSelecionado == "Essa semana (dom)") { 
  
          //Essa semana (dom) 
  
          this.dadosPeriodo.dataInicio = new Date(new Date().setDate(new Date().getDate() - new Date().getDay())) 
  
            .toISOString() 
  
            .substr(0, 10); 
  
          this.dadosPeriodo.dataFim = new Date().toISOString().substr(0, 10); 
  
        } else if (this.dadosPeriodo.periodoSelecionado == "Essa semana (seg)") { 
  
          //Essa semana (seg) 
  
          this.dadosPeriodo.dataInicio = new Date(new Date().setDate(new Date().getDate() - new Date().getDay() + 1)) 
  
            .toISOString() 
  
            .substr(0, 10); 
  
          this.dadosPeriodo.dataFim = new Date().toISOString().substr(0, 10); 
  
        } else if (this.dadosPeriodo.periodoSelecionado == "Semana passada (dom)") { 
  
          //Semana passada (dom) 
  
          this.dadosPeriodo.dataInicio = new Date(new Date().setDate(new Date().getDate() - new Date().getDay() - 7)) 
  
            .toISOString() 
  
            .substr(0, 10); 
  
          this.dadosPeriodo.dataFim = new Date(new Date().setDate(new Date().getDate() - new Date().getDay() - 1)) 
  
            .toISOString() 
  
            .substr(0, 10); 
  
        } else if (this.dadosPeriodo.periodoSelecionado == "Semana passada (seg)") { 
  
          //Semana passada (seg) 
  
          this.dadosPeriodo.dataInicio = new Date(new Date().setDate(new Date().getDate() - new Date().getDay() - 6)) 
  
            .toISOString() 
  
            .substr(0, 10); 
  
          this.dadosPeriodo.dataFim = new Date(new Date().setDate(new Date().getDate() - new Date().getDay())) 
  
            .toISOString() 
  
            .substr(0, 10); 
  
        } else if (this.dadosPeriodo.periodoSelecionado == "Este mês") { 
  
          //Este mês 
  
          this.dadosPeriodo.dataInicio = new Date(new Date().setDate(new Date().getDate() - new Date().getDate() + 1)) 
  
            .toISOString() 
  
            .substr(0, 10); 
  
          this.dadosPeriodo.dataFim = new Date().toISOString().substr(0, 10); 
  
        } else if (this.dadosPeriodo.periodoSelecionado == "Mês passado") { 
  
          //Mês passado 
  
          const dia = new Date(new Date().setDate(new Date().getDate() - new Date().getDate() + 1)); 
  
          this.dadosPeriodo.dataInicio = new Date(dia.setMonth(dia.getMonth() - 1)).toISOString().substr(0, 10); 
  
          this.dadosPeriodo.dataFim = new Date(new Date().setDate(new Date().getDate() - new Date().getDate())) 
  
            .toISOString() 
  
            .substr(0, 10); 
  
        } else if (this.dadosPeriodo.periodoSelecionado == "Este ano") { 
  
          //Este ano 
  
          var dataAtual = new Date(); 
  
          var ano = dataAtual.getFullYear(); 
  
          this.dadosPeriodo.dataInicio = ano + "-01-01"; 
  
          this.dadosPeriodo.dataFim = new Date().toISOString().substr(0, 10); 
  
        } else if (this.dadosPeriodo.periodoSelecionado == "Ano passado") { 
  
          //Ano Passado 
  
          var dataAtual = new Date(); 
  
          var ano = dataAtual.getFullYear() - 1; 
  
          this.dadosPeriodo.dataInicio = ano + "-01-01"; 
  
          this.dadosPeriodo.dataFim = ano + "-12-31"; 
  
        } 
  
      }, 
  
   
  
      validaData() { 
  
        this.dataFinalMenorInicial = this.dadosPeriodo.dataInicio > this.dadosPeriodo.dataFim ? true : false; 
  
        const dataAtual = new Date().toISOString().substr(0, 10); 
  
        this.dataFinalMaiorAtual = this.dadosPeriodo.dataFim > dataAtual ? true : false; 
  
   
  
        this.enviaComponentePai(); 
  
      }, 
  
   
  
      enviaComponentePai(dado) { 
  
        if (this.dadosPeriodo.periodoSelecionado != "Personalizado") { 
  
          this.$emit("dadosPeriodo", this.dadosPeriodo); 
  
        } 
  
        if (dado) { 
  
          this.$emit("dadosPeriodo", this.dadosPeriodo); 
  
        } 
  
      }, 
  
    }, 
  
  }; 
  
  </script> 
  
   
  
   
  
  CSS 
  
  .--is-flex-wrap { 
  
    display: flex !important; 
  
    flex-wrap: wrap; 
  
  } 