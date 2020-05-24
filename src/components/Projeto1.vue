<template>
    <div id="Projeto1">
        <div class="panel panel-default scores">
            <div class="playersScores item">
                <h1>Jogador</h1>
                <div class="progressBar">
                    <div class="progressBox" 
                        :class="{dangerScore: playerLife < 20}"
                        :style="{width: playerLife + '%'}"
                    ></div>
                </div>
                <div>
                    <p>{{ playerLife }} %</p>
                </div>
            </div>
            <div class="playersScores">
                <h1>Monstro</h1>
                <div class="progressBar">
                    <div class="progressBox" 
                        :class="{dangerScore: monsterLife < 20}"
                        :style="{width: monsterLife + '%'}"
                    ></div>
                </div>
                <div><p>{{ monsterLife }} %</p></div>
            </div>
        </div>

        <div class="panel panel-default result" v-if="hasResult">
            <div v-if="monsterLife == 0" class="win">
                <h2>Você ganhou!!! :)</h2>
            </div>
            <div v-else class="lose">
                <h2>Você perdeu! :(</h2>
            </div>
        </div>
        <div class="panel panel-default buttons">
            <button class="btn btn-danger">ATAQUE</button>
            <button class="btn btn-warning">ATAQUE ESPECIAL</button>
            <button class="btn btn-success">CURAR</button>
            <button class="btn btn-default">DESISTIR</button>
        </div>
        <div class="panel panel-default logs"></div>
    </div>
</template>

<script>
export default {
    data() {
        return {
            playerLife: 15,
            monsterLife: 100,
        }
    },

    computed: {
        hasResult() {
            return this.playerLife == 0 || this.monsterLife == 0;
        }
    }
}
</script>

<style>

html {
    font-family: 'Montserrat', sans-serif;
}

#Projeto1 {
    display: flex;
    flex-direction: column;
}

.panel {
    margin: 10px;
    padding: 20px;
    box-shadow: 0 2px 10px rgba(0,0,0,0.15);
}

.scores {
    display: flex;
    flex-direction: row;
    justify-content: space-around;
    text-align: center;
}

.scores .playersScores {
    flex : 1;
}

.scores .playersScores h1 {
    font-weight: 600;
}

.scores .progressBar {
	width: 85%;
	height: 30px;
    margin: auto;
	border: 1px solid #aaa;
}

.scores .progressBar .progressBox {
    height: 100%;
    background-color: green;
}

.scores .progressBar .progressBox.dangerScore {
    background-color: red;
}

.buttons {
    display: flex;
    flex-direction: row;
    justify-content: center;
}

.buttons button {
    margin-left: 1%;
    margin-right: 1%;
}

.result {
    display: flex;
    flex-direction: row;
    justify-content: center;
    text-align: center;
    font-size: 1.3rem;
    font-weight: 600;
}

.result .win {
    color: green;
}

.result .lose {
    color: red;
}
</style>