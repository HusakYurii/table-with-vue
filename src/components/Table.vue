<template>
    <main>
        <Navigation v-bind:navigation="navigation" v-on:onButtonClick="sortTableBy" v-on:onSearchInput="searchBy"/>
        <table class="table table-striped table-bordered">
            <TableHeader v-bind:header="header"/>
            <TableBody v-bind:body="body"/>
        </table>
    </main>
</template>

<script>
    import Navigation from './navigation/Navigation';
    import TableHeader from './tableHeader/TableHeader';
    import TableBody from './tableBody/TableBody';

    export default {
        name: "Table",
        components: {
            Navigation,
            TableHeader,
            TableBody
        },
        props: {
            data: Array
        },
        data() {
            return {
                navigation: {
                    sortRules: ["name", "location"],
                    sortStates: {
                        none: 0,
                        smToLg: 1,
                        lgToSm: 2
                    }
                },
                header: {
                    names: ["#", "name", "location", "currency"],
                },
                body: {
                    rows: this.data
                }
            }
        },
        methods: {
            sortTableBy(deta){
                //as a button clicked sort the table by `rule` and requested `sort state`
            },
            searchBy(value) {
                //as search data received sort the table by matched search strings
            }
        }
    }
</script>

<style scoped>

</style>