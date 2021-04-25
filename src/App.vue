<template>
    <div id="app">

        <div class="hover-grid">
            <GridItem></GridItem>
        </div>
    </div>

</template>

<script>
import GridItem from './components/grid/Item.vue'

export default {
    name: 'App',
    components: {
        GridItem
    },
    data() {
        return {
            griditems: [{
                label: 'Hoverable text'
            },
            {

            },
            ]
        }
    },
}
</script>

<style>
@import url('https://fonts.googleapis.com/css2?family=Noto+Sans+JP:wght@100&display=swap');

* {
    box-sizing: border-box;
    color: white;
    font-family: 'Noto Sans JP', sans-serif;
    letter-spacing: 2px;
}

body {
    background-color: black;
    display: flex;
    flex-flow: column wrap;
    justofy-content: center;
    align-items: center;
}

.hover-grid {
    border: 1px solid white;
    letter-spacing: 2px;
    color: white;
    display: grid;
    grid-template-columns: repeat(2, 1fr);
    align-items: stretch;
    text-align: center;
    grid-gap: 1rem;
    padding: 5rem;
}
</style>
