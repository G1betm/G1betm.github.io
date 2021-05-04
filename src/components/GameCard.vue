<template>
    <div class="game-cards" >
        <div class="card" v-for="(game, index) in gameInfo" :key="index">
            <div class="card-bg">
                <img :src="game.picture">
            </div>
            <div class="card-content">
                <div class="card-title">
                    {{game.name}}
                </div>
                <div class="card-text">
                    {{game.text}}
                </div>
                <div>
                    <a :href="game.name" class="card-btn link-hover">Learn more
                        <svg version="1.1" id="Capa_1" fill="#fff" xmlns="http://www.w3.org/2000/svg"
                            xmlns:xlink="http://www.w3.org/1999/xlink" x="0px" y="0px" width="20px" height="20px"
                            viewBox="0 0 123.964 123.964" style="enable-background:new 0 0 123.964 123.964;"
                            xml:space="preserve">
                            <g>
                                <path d="M121.7,57.681L83,26.881c-4-3.1-10-0.3-10,4.8v10.3c0,3.3-2.2,6.2-5.5,6.2H6c-3.3,0-6,2.4-6,5.8v16.2c0,3.2,2.7,6,6,6h61.5
		c3.3,0,5.5,2.601,5.5,5.9v10.3c0,5,6,7.8,9.9,4.7l38.6-30C124.7,64.781,124.8,60.081,121.7,57.681z" />
                            </g>
                        </svg>
                    </a>
                </div>

            </div>
        </div>
    </div>
</template>

<script>
    import axios from 'axios'

    export default {
        name: 'GameCard',
        props: {

        },
        data() {
            return {
                gameInfo: null,
                scrollValue: null,
            }
        },


        mounted() {
            axios
                .get('http://www.json-generator.com/api/json/get/cphrnSYoBK?indent=2')
                .then(response => (this.gameInfo = response.data));
        }
    }
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style lang="scss" scoped>
    .game-cards {
        display: flex;
        gap: 15px;
        padding-top: 150px;
        flex-wrap: wrap;

        .card {
            flex-basis: calc(50% - 15px);
            max-width: calc(50% - 15px);
            aspect-ratio: 16/9;
            background-color: #424242;
            color: #fff;
            display: flex;
            justify-content: center;
            align-items: center;
            position: relative;
            overflow: hidden;

            &-content {
                z-index: 2;
                display: flex;
                width: 100%;
                height: 100%;
                justify-content: center;
                flex-direction: column;
                transform: translate(-120%, 0);
                padding: 30px;
                transition: transform .3s ease;
                backdrop-filter: blur(10px) brightness(0.5);
            }

            &-title {
                font-size: 36px;
                margin-bottom: 20px;
            }

            &-text {
                font-size: 18px;
                line-height: 1.5;
            }

            &-btn {
                display: inline-flex;
                align-items: center;
                margin-top: 30px;

                svg {
                    margin-left: 10px;
                }
            }

            &-bg {
                position: absolute;
                left: 0;
                top: 0;
                width: 100%;
                height: 100%;
                transition: .3s ease-in;
            }
        }
    }

    .card:hover .card-content {
        transform: translate(0, 0);
    }
</style>