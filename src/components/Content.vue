<template xmlns:v-on="http://www.w3.org/1999/xhtml" xmlns:v-bind="http://www.w3.org/1999/xhtml">
    <div class="content">
        <ul>

            <my-block-component
                    index="0" v-on:change="changeCol(0)"  v-bind:col="colorsArray[colorCounter[0]]">
            </my-block-component>

            <my-block-component
                    index="1" v-on:change="changeCol(1)" v-bind:col="colorsArray[colorCounter[1]]">
            </my-block-component>

            <my-block-component
                    index="2" v-on:change="changeCol(2)" v-bind:col="colorsArray[colorCounter[2]]">
            </my-block-component>

            <my-block-component
                    index="3" v-on:change="changeCol(3)" v-bind:col="colorsArray[colorCounter[3]]">
            </my-block-component>

        </ul>
        
        <blend v-bind:pass='blendCols'></blend>
    </div>

</template>

<script>
    import ColorBlock from './ColorBlock.vue';
    import BlendBlock from './Blend.vue';

    export default {
        name: 'Content',
        data () {
            return {
                colorsArray: ['peachpuff', 'blue', 'green', 'pink'],
                colorCounter: {
                    0: 0,
                    1: 0,
                    2: 0,
                    3: 0
                },
                result: {
                    0: [255, 218, 185],
                    1: [255, 218, 185],
                    2: [255, 218, 185],
                    3: [255, 218, 185]
                },
                rgbMap: {
                    peachpuff: [255, 218, 185],
                    blue: [173, 216, 230],
                    green: [144, 238, 144],
                    pink: [255, 182, 193]
                },
                blendedCols: [255, 218, 185],
            }
        },
        methods: {

            // перевести строку цвета в формат ргб
            turnIntoRGB: function (index) {
                this.result[index] = this.rgbMap[this.colorsArray[this.colorCounter[index]]];
            },

            // получить средние значения
            getAverageNumbers: function () {
                // i is num of color in row; j is index
                for (var i = 0; i < 3; i++) {
                    var sum = 0;

                    for (var j = 0; j < 4; j++) {
                        sum = sum + this.result[j][i];
                    }

                    // calculate average nums
                    var average = (sum / 4) - ((sum / 4) % 1);

                    //push nums to blendedCols
                    this.blendedCols[i] = average;
                }
            },

            changeCol: function (num) {

                this.colorCounter[num] = (this.colorCounter[num] + 1) % this.colorsArray.length;
                this.turnIntoRGB(num);
            }
        },

        computed: {
            blendCols: function () {
                // TODO: тут вычисляется смешанный цвет на основе results
                this.getAverageNumbers();
                return [this.blendedCols[0], this.blendedCols[1], this.blendedCols[2]];
            }
        },

        components: {
            'my-block-component': ColorBlock,
            'blend': BlendBlock
        }
    }
</script>

<style scoped>
    .content {
        display: flex;
    }

    ul {
        margin: 0;
        padding: 0;
    }

</style>