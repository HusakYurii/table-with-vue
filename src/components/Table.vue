<template>
    <main>
        <Navigation v-bind:navigation="navigation" v-on:onButtonClick="sortTableBy" v-on:onSearchInput="searchBy"/>
        <table class="table table-striped table-bordered">
            <TableHeader v-bind:header="headers"/>
            <TableBody v-bind:rows="bodyData"/>
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
                    sortRules: ["Name", "Location"],
                    currRule: {
                        rule: "",
                        state: 0
                    },
                    SORT_STATES: {
                        NONE: 0,
                        SM_TO_LG: 1,
                        LG_TO_SM: 2
                    }
                },
                headers: ["#", "name", "location", "currency"],
                bodyData: []
            }
        },
        mounted() {
            this.bodyData = [...this.data];
        },
        methods: {
            sortTableBy({role}) {
                //as a button clicked sort the table by `rule` and requested `sort state`
            },
            searchBy({value}) {
                if (!value.trim()) {
                    this.bodyData = [...this.data];
                    return;
                }

                this.bodyData = this.data.filter(row => (
                    row.name.startsWith(value) ||
                    row.location.startsWith(value)
                ));
            }
        }
    }
</script>

<style scoped>

</style>