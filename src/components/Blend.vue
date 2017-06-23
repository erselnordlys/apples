<template xmlns:v-on="http://www.w3.org/1999/xhtml" xmlns:v-bind="http://www.w3.org/1999/xhtml">

    <ul>
        <li><div class="button" v-on:click="blend"> {{ msg }} </div></li>
        <!--{{ col }}-->

        <li><div class="result-block" v-bind:style="{ background: result }"></div></li>
    </ul>


    </div>
</template>

<script>
    import myContent from './Content.vue';

    var colorsArray = [];
    var blendedCol = [];
    var result;

    export default {
        name: 'BlendBlock',
        data () {
            return {
                msg: 'Blend colors.',
                rgbMap: {
                    peachpuff: [255, 218, 185],
                    blue: [173, 216, 230],
                    green: [144, 238, 144],
                    pink: [255, 182, 193]
                },
                result: result
            }
        },
        methods: {
            getAllColors: function () {
                // записать все окончательные цвета
                colorsArray[0] = this.col0;
                colorsArray[1] = this.col1;
                colorsArray[2] = this.col2;
                colorsArray[3] = this.col3;
            },

            blend: function () {
                this.getAllColors();

                // записать смешанный цвет в blendedCol
                for (var i = 0; i < 3; i++) {
                    blendedCol[i] = (this.rgbMap[colorsArray[0]][i] + this.rgbMap[colorsArray[1]][i]
                        + this.rgbMap[colorsArray[2]][i] + this.rgbMap[colorsArray[3]][i]) / colorsArray.length;

                    // округлить числа
                    if (blendedCol[i] % 1 !== 0) {
                        blendedCol[i] = blendedCol[i] - blendedCol[i] % 1;
                    }
                }

                this.result = ' rgb(' + blendedCol[0] + ', ' + blendedCol [1] + ', ' + blendedCol[2] + ') ' ;

                console.log('blended col: ' + blendedCol);
                console.log('result: ' + this.result);
            }
        },
        props: ['col0', 'col1', 'col2', 'col3'],

        components: {}
    }
</script>

<style scoped>
    div {
        width: 200px;
        border: 1px solid grey;
        border-radius: 5px;
        display: flex;
        align-items: center;
        justify-content: center;
        margin-bottom: 10px;
    }

    ul {
        list-style: none;
        margin-left: 10px;
    }

    li {
        padding: 0;
    }
    .button {
        height: 40px;
        background: whitesmoke;
        cursor: pointer;

    }

    .result-block {
        height: 144px;
        background: rgb(255, 255, 255);
    }
</style>