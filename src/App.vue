<template>
    <div id="app">
        <GridContainer></GridContainer>
    </div>
</template>

<script>
import GridContainer from './components/grid/Container.vue'

export default {
    name: 'App',
    components: {
        GridContainer
    }
}
</script>

<style>
@import url('https://fonts.googleapis.com/css2?family=Noto+Sans+JP:wght@100&display=swap');

* {
    box-sizing: border-box;
    color: BLACK;
    font-family: 'Noto Sans JP', sans-serif;
    letter-spacing: 2px;
}

body {
    background-color: #facbba;
    display: flex;
    flex-flow: column wrap;
    justify-content: center;
    align-items: center;
    height: 100vh;
}
</style>
