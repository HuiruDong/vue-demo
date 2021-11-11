<template>
    <div class="container">
        <div
            class="card"
            v-for="item in renderCards"
            :key="item"
            :style="{ background: item }"
        ></div>
    </div>
</template>

<script>
export default {
    name: 'HelloWorld',
    props: {
        msg: String,
    },
    data() {
        return {
            cards: [
                'lightblue',
                'lightcoral',
                'lightgray',
                'lightpink',
                'lightsalmon',
                'lightseagreen',
            ],
            renderCards: [],
        };
    },
    created() {
        this.renderCards = JSON.parse(JSON.stringify(this.cards));
    },
    mounted() {
        this.changeCards(document.body.clientWidth);
        window.onresize = () => {
            this.changeCards(document.body.clientWidth);
        };
    },
    methods: {
        changeCards(width) {
            if (width <= 1200) {
                this.renderCards = JSON.parse(JSON.stringify(this.cards)).slice(0, 4);
            } else if (width <= 1440) {
                this.renderCards = JSON.parse(JSON.stringify(this.cards)).slice(0, 5);
            } else {
                this.renderCards = JSON.parse(JSON.stringify(this.cards));
            }
        },
    },
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
.container {
    height: 200px;
    display: flex;
    flex-wrap: nowrap;
}
.container div {
    flex: 1;
}
</style>
