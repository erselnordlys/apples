<template xmlns:v-on="http://www.w3.org/1999/xhtml" xmlns:v-bind="http://www.w3.org/1999/xhtml">

    <div id="app">
        <h1>{{ msg }}</h1>
        <main-content/>
    </div>

</template>

<script>

    import Content from './components/Content.vue';

    export default {
        name: 'app',
        data () {
            return {
                msg: 'Click on block to change its color.',
            }
        },
        components: {
            'main-content': Content
        }
    }

</script>


<style>

    #app {
        font-family: 'Avenir', Helvetica, Arial, sans-serif;
        -webkit-font-smoothing: antialiased;
        -moz-osx-font-smoothing: grayscale;
        text-align: center;
        color: #2c3e50;
        margin-top: 60px;

        display: flex;
        align-items: center;
        flex-direction: column;
    }

    h1, h2 {
        font-weight: normal;
    }

</style>