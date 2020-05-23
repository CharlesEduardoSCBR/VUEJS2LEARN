<template>
    <div id="desafio4" class="container-fluid">
        <!-- 1) Iniciar a execução do efeito usando botão. 
        O efeito deve alternadamente trocar as classes "destaque" e
        "encolher" para cada chamada de setInteval. Use a div abaixo
        com id "efeito" para associar as classes CSS. -->
        <h2>#01</h2>
        <div>
            <button @click="iniciarEfeito">Iniciar Efeito</button>
            <div id="efeito" :class="classeIniciarEfeito"></div>
        </div>
        
        <!-- 2) Crie duas classes CSS e associe a div usando a
            sintaxe de array -->
        <h2>#02</h2>
        <div :class="divSemClasse">Estou sem classe CSS :(</div>

        <!-- 3) Aplique na div abaixo a classe informada pelo usuário
            (crie classe CSS de exemplo). -->
        <h2>#03</h2>
        <div>
            <input type="text" v-model="divUser">
            <div :class="divUser"></div>
        </div>

        <!-- 4) Aplique na div abaixo a classe informada pelo usuário e
        outra classe usando o valor true/false (crie classes CSS de exemplo). -->
        <h2>#04</h2>
        <div>
            <input type="text" v-model='divUserNew'>
            <input type="text" @input="setdivAlgumaCoisa">
            <div :class="[divUserNew, {divAlgumaCoisa}]"></div>
        </div>

        <!-- 5) Repita 3) mas utilizando estilos ao invés de classes CSS.
        Associe os estilos a div abaixo  -->
        <h2>#05</h2>
        <div>
            <input type="text" v-model="cor">
            <div :style="[estilo, {backgroundColor: cor}]"></div>
        </div>

        <!-- 6) Crie uma barra de progresso simples com setInterval 
        e binding de estilo. -->
        <h2>#06</h2>
        <div>
            <button>Iniciar</button>
            <div></div>
        </div>
    </div>
</template>

<script>
export default {
    name : 'desafio4',
    
    data() {
        return {
                classeIniciarEfeito : 'destaque',
                divSemClasse : [
                    'fontEstiloPadrao', 'divAlgumaCoisa'
                ],
                divAlgumaCoisa : true,
                divUser : '',
                divUserNew : '',

                cor : '',

                estilo: {
                    width : '50px',
                    height: '50px',
                }
            }
    },

    methods: {
        iniciarEfeito() {
            setInterval(() => {
                this.classeIniciarEfeito = (this.classeIniciarEfeito == 'destaque' ? 'encolher' : 'destaque');
            }, 1000);
        },

        setdivAlgumaCoisa(event) {
            
            if(event.target.value == "true"){
                this.divAlgumaCoisa = true;
            }
            
            if(event.target.value == "false"){
                this.divAlgumaCoisa = false;
            }
        }
    }


}
</script>

<style>
#efeito {
	width: 100px;
	height: 100px;
	border: 1px solid black;
}

.destaque {
	background-color: red;
	width: 200px !important;
}

.encolher {
	background-color: gray;
	width: 50px !important;
}

.fontEstiloPadrao {
    font-family: Cambria, Cochin, Georgia, Times, 'Times New Roman', serif;
    font-size : 18px;
    color: red;
}

.divAlgumaCoisa {
    background-color: yellow;
    border: 1px solid black;
    width: 150px;
    height: 50px;
}

.direita {
    float: right;
}
</style>