<template>
    <div>
        <div class="hover-btn" id="1">This is a windows 10 hoverable item</div>
    </div>
</template>

<script>
export default {
    name: 'GridItem',
    props: {
        msg: String
    }

}
</script>

<style lang="scss" scoped>
.hover-btn {
    padding: 2rem;
    text-align: center;
    border: none;
    border-radius: 0px;
    background: black;
    color: white;
    border: 1px solid transparent;
}

button:focus {
    outline: none;
}
</style>
