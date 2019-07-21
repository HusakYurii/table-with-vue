<template>
    <thead>
        <tr>
            <th v-for="header in headers" scope="col">{{header}}</th>
        </tr>
    </thead>
</template>

<script>
    export default {
        name: "TableHeader",
        props: {
            headers: Array
        }
    }
</script>

<style scoped>

</style>