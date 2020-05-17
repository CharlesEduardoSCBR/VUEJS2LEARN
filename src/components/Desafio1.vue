<template>
  <div id="desafio1" class="container-fluid">
      <div class="row-fluid">
            <!-- 1) Preencha a tag <p> abaixo com o seu Nome e Idade - usando Interpolação -->
            <p class="
                        col-lg-offset-1 col-lg-11
                        col-md-offset-1 col-md-11
                        col-sm-offset-1 col-sm-11
                        col-xs-offset-1 col-xs-11
                     "
            >Usando VueJS - {{ person.name }} ({{ person.age }})</p>

            <!-- 2) Exiba sua idade multiplicada por 3 -->
                        <p class="
                        col-lg-offset-1 col-lg-11
                        col-md-offset-1 col-md-11
                        col-sm-offset-1 col-sm-11
                        col-xs-offset-1 col-xs-11
                     "
            >
             {{ person.age * 3 }}
            </p>

            <!-- 3) Chame uma função para exibir um número randomico
                entre 0 and 1 (Math.random()) -->
            <p></p>

            <!-- 4) Procure uma imagem no google e exiba na tag img 
                fazendo o binding no atributo "src" -->
            <div>
                <img height="400">
            </div>

            <!-- 5) Inicialize o input com o seu nome (use o atributo "value") -->
            <div>
                <input type="text">
            </div>
        </div>
    </div>
</template>

<script>
export default {
    name: 'desafio1',
    data(){
        return {
            person : {
                name : 'José Silva',
                age : 20,
            },
        }
    }

}
</script>

<style>

</style>