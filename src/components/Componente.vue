<template>
    <div>
        <div class="caixa">
            <h1>GATO</h1>
        </div>

        <div class="box">
            <h1>GATO</h1>
        </div>

        <p>Lorem ipsum dolor et </p>

        <button class="button">Button</button>
        <button class="button is-primary is-large">Button</button>


        <div class="columns is-fullwidth">
            <div class="column is-5">
                <div class="box">CAIXA1</div>
            </div>
            <div class="column auto">
                <div class="box">CAIXA2</div>
            </div>
        </div>

        {{ variavelUm }}
        


    </div>
</template>

<script>

export default {
    name: 'Primeiro',
    data() {
        return {
            variavelUm: 'uma frase',
            variavelDois: null
        }
    },



}
</script>

<style scooped>

</style>

