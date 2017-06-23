<template xmlns:v-on="http://www.w3.org/1999/xhtml" xmlns:v-bind="http://www.w3.org/1999/xhtml">

    <div class="block"
         v-on:click="change" v-bind:class='col'> {{ index }}
    </div>

</template>

<script>

    var sendColor = 'peachpuff';

    export default {
        name: 'ColorBlock',

        props: ['index', 'col'],
        data () {
            return {
                colorsArray: ['peachpuff', 'blue', 'green', 'pink'],
                color: 'peachpuff'
            }
        },
        methods: {
            change: function () {
                this.$emit('change');
                console.log('index: '+  this.index);

            }
        }
    }
</script>

<style>
    .block {
        width: 400px;
        height: 40px;
        border: 1px solid grey;
        border-radius: 5px;
        display: flex;
        align-items: center;
        justify-content: center;
        margin-bottom: 10px;
        cursor: pointer;
    }

    .peachpuff {
        background-color: rgb(255, 218, 185);
    }

    .blue {
        background-color: rgb(173, 216, 230);
    }

    .green {
        background-color: rgb(144, 238, 144);
    }

    .pink {
        background-color: rgb(255, 182, 193);
    }
</style>