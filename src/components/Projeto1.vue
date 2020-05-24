<template>
    <div id="Projeto1">
        <div class="panel panel-default scores"></div>
        <div class="panel panel-default result"></div>
        <div class="panel panel-default buttons"></div>
        <div class="panel panel-default logs"></div>
    </div>
</template>

<script>
export default {
    el: "Projeto1",
    data() {
        return {

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

</style>