<template>
    <div id="Projeto1">
        <div class="panel panel-default scores">
            <div class="playersScores item">
                <h1>Jogador</h1>
                <div class="progressBar">
                    <div class="progressBox" :style="[{backgroundColor:color}]"></div>
                </div>
                <div>
                    <p>{{ playerLife }} %</p>
                </div>
            </div>
            <div class="playersScores">
                <h1>Monstro</h1>
                <div class="progressBar">
                    <div class="progressBox" :style="[{backgroundColor:color}]"></div>
                </div>
                <div><p>{{ monsterLife }} %</p></div>
            </div>
        </div>

        <div class="panel panel-default result"></div>
        <div class="panel panel-default buttons"></div>
        <div class="panel panel-default logs"></div>
    </div>
</template>

<script>
export default {
    data() {
        return {
            playerLife: 100,
            monsterLife: 100,
            color : "green",
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

.progressBar {
	width: 85%;
	height: 30px;
    margin: auto;
	border: 1px solid black;
}

.progressBox {
    height: 100%;
}

</style>