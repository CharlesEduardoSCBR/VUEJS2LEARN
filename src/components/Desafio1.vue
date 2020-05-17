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
            <p class="
                        col-lg-offset-1 col-lg-11
                        col-md-offset-1 col-md-11
                        col-sm-offset-1 col-sm-11
                        col-xs-offset-1 col-xs-11
                     "
            >
            {{ random() }}
            </p>

            <!-- 4) Procure uma imagem no google e exiba na tag img 
                fazendo o binding no atributo "src" -->
            <div class="
                        col-lg-offset-1 col-lg-11
                        col-md-offset-1 col-md-11
                        col-sm-offset-1 col-sm-11
                        col-xs-offset-1 col-xs-11
                       "
            >
                <img height="400" :src="image">
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
            image : 'data:image/jpeg;base64,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'
        }
    },

    methods:{
        random() {
            return Math.random();
        }
    }

}
</script>

<style>

</style>