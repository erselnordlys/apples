<template xmlns:v-on="http://www.w3.org/1999/xhtml" xmlns:v-bind="http://www.w3.org/1999/xhtml">

    <div class="block"
         v-on:click="change" v-bind:class='col'> {{ msg + index}}
    </div>

</template>

<script>
    import Blend from './Blend.vue';

    export default {
        name: 'ColorBlock',
        props: ['index', 'col'],
        data () {
            return {
                msg: 'Block #'
            }
        },
        methods: {
            change: function () {
                this.$emit('change');
            }
        },


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
        user-select: none;
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