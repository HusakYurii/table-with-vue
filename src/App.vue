<template>
    <div id="app">
        <Table v-bind:data="data"/>
    </div>
</template>

<script>
    import Table from './components/Table';
    import data from "./db/data";

    export default {
        name: 'app',
        components: {
            Table
        },
        data(){
            return {
                data
            }
        }
    }
</script>

<style>
	#app {
		min-width: 630px;
	}
</style>
