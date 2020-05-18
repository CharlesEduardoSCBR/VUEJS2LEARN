<template>
    <div id="desafio3" class="container-fluid">
        <!-- 1) Exibir em "resultado" o texto 'Valor Diferente' enquanto
               "valor" for diferente de 37 - "valor" é alterado pelos botões.
               Mostrar 'Valor Igual' quando "valor" for igual a 37 -->

        <!-- 2) Monitorar as mudança de "resultado" e reiniciar "valor"
            para 0 depois de 5 segundos (dica: setTimeout(..., 5000) -->            
        <div class="row-fluid">
            <p class="
                        col-lg-offset-1 col-lg-11
                        col-md-offset-1 col-md-11
                        col-sm-offset-1 col-sm-11
                        col-xs-offset-1 col-xs-11"
            >Valor atual: {{ valor }}</p>
            <button @click="valor += 5"
                class=
                    "
                        col-lg-offset-1 col-lg-1
                        col-md-offset-1 col-md-1
                        col-sm-offset-1 col-sm-3
                        col-xs-12
                        btn btn-primary
                    "
            >Somar 5</button>
            <button @click="valor += 1"
                class=
                    "
                        col-lg-1 col-lg-offset-1
                        col-md-1 col-md-offset-1
                        col-sm-3 col-sm-offset-1
                        col-xs-12
                        btn btn-primary
                    "
            >Somar 1</button>
            <p class="
                        col-lg-offset-1 col-lg-11
                        col-md-offset-1 col-md-11
                        col-sm-offset-1 col-sm-11
                        col-xs-offset-1 col-xs-11
                    "
            >{{ resultado }}</p>
        </div>
    </div>  
</template>

<script>
export default {
    name: 'desafio3',
    data() {
        return {
            valor : 0,
        }
    },

    computed: {
        resultado(){
            return this.valor != 37 ? 
                'Valor Diferente' : 'Valor Igual';
        }
    },

    watch: {
        valor(){
            setTimeout(() =>{
                this.valor = 0;
            }, 2000);
        }
    },
}
</script>

<style>

</style>