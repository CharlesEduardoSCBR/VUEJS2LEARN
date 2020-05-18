<template>
    <div id="desafio2" class="container-fluid">
      <div class="row-fluid">
        <!-- 1) Exiba um alert quando o botão for clicado -->
        <div>
            <button v-on:click="showAlert()" >Exibir Alerta</button>
        </div>

        <!-- 2) Escute o evento "keydown" e armazene o valor na propriedade
            data (dica: event.target.value) -->
        <div>
            <input type="text"
                v-on:keydown="listenKeys($event)"
            >
            <p>{{ valor }}</p>
        </div>

        <!-- 3) Ajuste o exemplo 2 para disparar o evento "keydown" somente
            quando a tecla for ENTER -->
        <div>
            <input type="text">
            <p>{{ valor }}</p>
        </div>
      </div>
    </div>
</template>

<script>
export default {
     name: 'desafio2',

     data() {
         return {
             valor : 0,
         }
     },

     methods: {
         showAlert(){
             alert('The alert was triggered');
         },

         listenKeys(event){
             this.valor = event.target.value;
         },
     }
}
</script>

<style>

</style>