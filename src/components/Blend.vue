<template xmlns:v-on="http://www.w3.org/1999/xhtml" xmlns:v-bind="http://www.w3.org/1999/xhtml">

    <ul>
        <div class="result-block" v-bind:style=" { background: getColor} ">{{ pass }}</div>
    </ul>


</template>

<script>
    import myContent from './Content.vue';
    import colorBlock from './ColorBlock.vue';


    export default {
        name: 'BlendBlock',
        data () {
            return {
                msg: 'Blend colors.'
            }
        },
        props: ['pass'],
        computed: {
          getColor: function () {
              return ('rgb(' + this.pass[0] + ', ' + this.pass[1] + ', ' + this.pass[2] + ')');
          }
        }
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
        /*margin-bottom: 10px;*/
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
        height: 196px;
    }
</style>