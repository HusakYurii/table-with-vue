<template>
    <tbody>
        <tr v-for="(row, indx) in rows" v-bind:key="row.id">
            <th scope="row">{{ `${indx + 1}` }}</th>
            <td>{{row.name}}</td>
            <td>{{row.location}}</td>
            <td>{{row.currency}}</td>
        </tr>
    </tbody>
</template>

<script>
    export default {
        name: "TableBody",
        props: {
            rows: Array
        }
    }
</script>

<style scoped>

</style>