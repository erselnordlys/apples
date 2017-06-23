<template xmlns:v-on="http://www.w3.org/1999/xhtml" xmlns:v-bind="http://www.w3.org/1999/xhtml">
    <div class="content">
        <ul>

            <my-block-component
                    index="0" v-on:change="changeCol(0)"  v-bind:col="result[0]">
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

        <blend :col0="result[0]" :col1 ="result[1]" :col2="result[2]" :col3="result[3]"></blend>

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
                    0: 'peachpuff',
                    1: 'peachpuff',
                    2: 'peachpuff',
                    3: 'peachpuff'
                }
            }
        },

        props: {
            col: String,
            index: Number,
            resultColor: Object,
            col0: String,
            col1: String,
            col2: String,
            col3: String
        },
        methods: {
            changeCol: function (num) {

                this.colorCounter[num]++; // add 1 to block counter

                this.result[num] = this.colorsArray[this.colorCounter[num]];

                if (this.colorCounter[num] > this.colorsArray.length - 1) {
                    this.colorCounter[num] = 0;
                    this.result[num] = this.colorsArray[this.colorCounter[num]];

                }

                console.log('color is: ' + this.result[num]);
                console.log('counter: ' + this.colorCounter[num]);

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