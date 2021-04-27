<template>
    <div class="hover-grid" ref="hovergrid">
        <GridItem v-for="(item, index) in gridItems" :key="index" :msg="item.label" :num="index"></GridItem>
    </div>
</template>

<script>
import GridItem from './Item.vue'

export default {
    name: "GridContainer",
    components: {
        GridItem
    },
    data() {
        return {
            gridItems: [{
                label: 'Hoverable text'
            },
            {
                label: 'Hoverable text'
            },
            {
                label: 'Hoverable text'
            },
            {
                label: 'Hoverable text'
            },
            {
                label: 'Hoverable text'
            },
            {
                label: 'Hoverable text'
            },
            {
                label: 'Hoverable text'
            },
            {
                label: 'Hoverable text'
            },
            {
                label: 'Hoverable text'
            },
            {
                label: 'Hoverable text'
            },
            {
                label: 'Hoverable text'
            },
            {
                label: 'Hoverable text'
            }]
        }
    },
    mounted() {
        const offset = 69;
        const angles = []; //in deg
        for (let i = 0; i <= 360; i += 45) {
            angles.push((i * Math.PI) / 180);
        }
        let nearBy = [];

        const body = this.$refs.hovergrid;

        body.addEventListener("mousemove", (e) => {
            const x = e.x; //x position within the element.
            const y = e.y; //y position within the element.

            // Removes all items from nearBy and removes borderImage
            nearBy.splice(0, nearBy.length).forEach((e) => (e.style.borderImage = null));

            // .reduce is different from .map or .foreEach in that it runs operation on each item AND pushes them to the array
            nearBy = angles.reduce((acc, rad, i, arr) => {
                const cx = Math.floor(x + Math.cos(rad) * offset);
                const cy = Math.floor(y + Math.sin(rad) * offset);
                const element = document.elementFromPoint(cx, cy);

                if (element !== null) {

                    if (element.className === "hover-btn" && acc.findIndex((ae) => ae.id === element.id) < 0) {
                        const brect = element.getBoundingClientRect();
                        const bx = x - brect.left; //x position within the element.
                        const by = y - brect.top; //y position within the element.

                        if (!element.style.borderImage)
                            element.style.borderImage = `radial-gradient(${offset * 2}px ${offset * 2
                                }px at ${bx}px ${by}px ,rgba(118,96,146,0.7),rgba(255,177,185,0.1),transparent ) 9 / 1px / 0px stretch `;
                        return [...acc, element];
                    }
                }
                return acc;
            }, []);
        })
    }
}
</script>

<style lang="scss" scoped>
.hover-grid {
    border: 1px solid white;
    letter-spacing: 2px;
    color: white;
    display: grid;
    grid-template-columns: repeat(3, 1fr);
    align-items: stretch;
    text-align: center;
    grid-gap: 1rem;
    padding: 5rem;
}
</style>
