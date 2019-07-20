<template>
    <thead>
        <tr>
            <th v-for="name in names" scope="col">{{name}}</th>
        </tr>
    </thead>
</template>

<script>
    export default {
        name: "TableHeader",
        props: {
            header: Object
        },
        data(){
            return {
                names: this.header.names
            }
        }
    }
</script>

<style scoped>

</style>