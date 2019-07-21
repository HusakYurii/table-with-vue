<template>
    <main>
        <Navigation v-bind:navigation="navigation" v-on:onButtonClick="sortTableBy" v-on:onSearchInput="searchBy"/>
        <table class="table table-striped table-bordered">
            <TableHeader v-bind:header="headers"/>
            <TableBody v-bind:rows="data"/>
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
                    sortRules: [ "Name","Location" ],
                    SORT_STATES: {
                        NONE: 0,
                        SM_TO_LG: 1,
                        LG_TO_SM: 2
                    }
                },
                headers: ["#", "name", "location", "currency"]
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