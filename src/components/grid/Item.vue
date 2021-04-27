<template>
    <div class="hover-btn" :id="num" ref="hoverItem">{{ msg }}</div>
</template>

<script>
export default {
    name: 'GridItem',
    props: {
        msg: String,
        num: Number,
    },
    mounted() {
        const el = this.$refs.hoverItem

        el.onmouseleave = () => {
            el.style.background = "#facbba";
            el.style.borderImage = null;
        };

        el.addEventListener("mousemove", (e) => {
            const rect = e.target.getBoundingClientRect();
            const x = e.clientX - rect.left; //x position within the element.
            const y = e.clientY - rect.top; //y position within the element.
            el.style.background = `radial-gradient(circle at ${x}px ${y}px , rgba(255,177,185,0.7),rgba(255,177,185,0) )`;
            el.style.borderImage = `radial-gradient(20% 75% at ${x}px ${y}px ,rgba(255,177,185,0.7),rgba(255,177,185,0.1) ) 1 / 1px / 0px stretch `;
        });
    }
}
</script>

<style lang="scss" scoped>
.hover-btn {
    padding: 2rem;
    text-align: center;
    border: none;
    border-radius: 0px;
    background: #facbba;
    color: black;
    border: 1px solid transparent;
}

button:focus {
    outline: none;
}
</style>
