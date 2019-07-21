<template>
    <main>
        <Navigation v-bind:navigation="navigation" v-on:onButtonClick="sortTableBy" v-on:onSearchInput="searchBy"/>
        <table class="table table-striped table-bordered">
            <TableHeader v-bind:headers="headers"/>
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
                navigation: ["Name", "Location"],
                SORT_STATES: {
                    CURR: 1,
                    SM_TO_LG: -1,
                    LG_TO_SM: 1
                },
                headers: ["#", "Name", "Location", "Currency"],
                bodyData: []
            }
        },
        mounted() {
            this.bodyData = [...this.data];
        },
        methods: {
            sortTableBy({role}) {
                this.setNewState();

                const {SM_TO_LG, LG_TO_SM, CURR} = this.SORT_STATES;

                switch (CURR) {
                    case SM_TO_LG:
                        this.bodyData.sort((a, b) => a[role] > b[role] ? 1 : -1);
                        break;
                    case LG_TO_SM:
                        this.bodyData.sort((a, b) => a[role] < b[role] ? 1 : -1);
                        break;
                    default:
                        console.warn(`Something went wrong for sorting rule: ${role}, state ${state}`)
                }
            },
            setNewState() {
                this.SORT_STATES.CURR *= -1;
            },
            searchBy({value}) {
                value = value.trim().toLowerCase();

                if (!value) {
                    this.bodyData = [...this.data];
                    return;
                }

                this.bodyData = this.data.filter(row => (
                    row.name.toLowerCase().startsWith(value) ||
                    row.location.toLowerCase().startsWith(value)
                ));
            }
        }
    }
</script>

<style scoped>

</style>