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
            <template v-if="startGame">
                <button @click="attack(false)" class="btn btn-danger"  >ATAQUE</button>
                <button @click="attack(true)" class="btn btn-warning" >ATAQUE ESPECIAL</button>
                <button @click="healAndHurt" class="btn btn-success" >CURAR</button>
                <button 
                    @click="startGame=false"
                    class="btn btn-default" >DESISTIR</button>
            </template>
            <template v-else>
                <button @click="run"
                    class="btn btn-primary">Iniciar o jogo</button>
            </template>
        </div>
        <div class="panel panel-default logs" v-if="logs.length > 0">
            <ul>
                <li v-for="(log, index) in logs" class="log" :class="log.cls" :key="index">{{ log.text }}</li>
            </ul>
        </div>
    </div>
</template>

<script>
export default {
    data() {
        return {
            startGame: false,
            playerLife: 100,
            monsterLife: 100,
            logs : []
        }
    },

    methods: {
        run(){
            this.startGame = true;
            this.playerLife = 100;
            this.monsterLife = 100;
            this.logs = [];
        },

        attack(especial = false){
            this.hurt('playerLife', 5,10,especial, 'Jogador', 'Monstro', 'player');

            if (this.monsterLife > 0) {
                this.hurt('monsterLife', 7,12,false, 'Monstro', 'Jogador', 'monster');
            }
        },

        hurt(atacante, min, max, especial, source, target, cls){
            let plus = especial ? 5 : 0;
            let hurt = (this.getRandom(min+plus, max+plus));

            this[atacante] = Math.max(this[atacante] - hurt, 0);
            this.registerLog(`${source} atingiu ${target} com ${hurt}.`, cls);
        },

        heal(min, max){
            let heal = this.getRandom(min, max);
            
            this.playerLife = Math.min(this.playerLife + heal, 100);
            this.registerLog(`Jogador ganhou força de ${heal}.`, 'player');
        },

        healAndHurt(){
            this.heal(10, 15);
            this.hurt('playerLife', 7, 12, false, 'Monstro', 'Jogador', 'monster');
        },

        getRandom(min, max){
            const value = Math.random() * (max - min) + min;
            return Math.round(value);
        },

        registerLog(text, cls) {
            this.logs.unshift({ text, cls});
        }
    },

    computed: {
        hasResult() {
            return this.playerLife == 0 || this.monsterLife == 0;
        }
    },

    watch: {
        hasResult(value){
            if(value) this.startGame = false;
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
    text-transform: uppercase;
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

div .logs ul {
    display: flex;
    flex-direction: column;
    list-style: none;
    padding: 0;
    margin: 0;
}

div .logs ul li {
    display: flex;
    justify-content: center;
    margin: 4px 0px;
    padding: 3px 0px;
    font-weight: 600;
    font-size: 1.5rem;
    text-transform: uppercase;
    border-radius: 3px;
}

div .logs .player {
    background-color: #5cb85caa;
}

div .logs .monster {
    background-color: #d9534faa;
}

</style>