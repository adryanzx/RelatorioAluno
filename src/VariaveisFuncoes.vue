<template>
    <div>

        {{ CiclodeVida }}

        <button class="button is-danger"  @click="HabilitarFrase()">Clique Aqui!!</button>
        <span v-if="mostrar">Parabéns, você ganhou 1 bala 7Belo!!</span>
        <span v-else>Poxa, clica aeeeee!</span>

        
    </div>

    <!-- mostrar == true É A MESMA COISA QUE COLOCAR SÓ mostrar dentro do if -->

</template>


<script>
export default {
    name: 'VariaveisFuncoes',
    //componentes: {},
    data() {
        return {
            mostrar: false,  // TODA VEZ QUE FOR REFERENCIAR UMA VARIAVEL DO "DATA()" UTILIZAR THIS.(NOMEVARIAVEL)
            CiclodeVida: null
        }
    },
    methods:{
        HabilitarFrase() {
            this.mostrar = true
        },
        // aqui dentro ficam todas as funções, separadas por vírgula
    },
}
</script>


<!-- Estudar methods dentro de Vue e como modificar variáveis dentro das funções
 Dentro de Vue: v-if, v-for 
@click e @change
Estudar o ciclo de vida de uma aplicação VUE e como ela pode ser utilizada em uma aplicação.

Para subir o código no git:
git add .
git commit -m "escreva aqui uma mensagem para saber o que foi feito no código"
git push origin "coloque o link do repositório, lembrando que vc precisa ter autorização
para fazer o commit"-->
