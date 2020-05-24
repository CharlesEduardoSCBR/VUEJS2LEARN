<template>
    <div id="desafio6" class="container-fluid">
        <!-- 1) Ligue o botão para alternar a exibição dos dois
        parágrafos. Use ambos v-if e v-show e inspecione os elementos
        para ver a diferença -->
        <h2>#01</h2>
        <div>
            <button @click="expressao = !expressao">Alternar</button>
            <p v-if="expressao">Você quer me ver ...</p>
            <p v-else>...ou eu</p>
            <p v-show="expressao">Você quer me ver ...</p>
            <p v-show="!expressao">...ou eu</p>
        </div>

        <!-- 2) Exiba em uma <ul> um array de elementos da sua escolha.
        Imprima também o índice de cada elemento. -->
        <h2>#02</h2>
        <ul>
            <li v-for="(nome, i) in nomes" :key="i">
                {{ nome }} - {{ i }}
            </li>
        </ul>

        <!-- 3) Imprimir todos os pares de valor-chave do objeto a seguir:
        {
			titulo: 'O Senhor dos Anéis',
			autor: 'J.R.R. Tolkiens',
			volume: '3'
		}
        Imprima também o índice de cada item. -->
        <h2>#03</h2>
        <ul>
            <li v-for="(valor, chave, indice) in livro" :key="indice">
                {{ chave }}: {{ valor }} - {{ indice + 1 }}
            </li>
        </ul>
    
        <!-- 4) Imprima o seguinte objeto (somente os valores) e
        também crie um loop aninhado para o array:
        {
			10,
			: 'Maria',
			s: [7.67, 8.33, 6.98, 9.21]
		}
        (dica: use v-for e v-if na resolução) -->
        <h2>#04</h2>
        <ul>
            <li v-for="valor in aluno" :key="valor">
                <template v-if="!Array.isArray(valor)">
                    {{ valor }}
                </template>
                <template v-else>
                    Notas:
                    <ul>
                        <li v-for="nota in valor" :key="nota">{{ nota }}</li>
                    </ul>
                </template>
            </li>
        </ul>
    </div>
</template>

<script>
export default {
    el: '#desafio6',
	data() {
        return {
            expressao: true,
            nomes: ['Ana', 'Rafa', 'Lucas', 'Gui'],
            livro: {
                titulo: 'O Senhor dos Anéis',
                autor: 'J.R.R. Tolkiens',
                volume: '3'
            },
            aluno: {
                id: 10,
                nome: 'Maria',
                notas: [7.67, 8.33, 6.98, 9.21]
            }
        }
    }
}
</script>

<style>

</style>