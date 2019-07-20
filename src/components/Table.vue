<template>
    <main>
        <Navigation v-bind:navigation="navigation"/>
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
                    sortRules: ["name", "location"]
                },
                header: {
                    names: ["#", "name", "location", "currency"],
                },
                body: {
                    rows: this.data
                }
            }
        }
    }
</script>

<style scoped>

</style>