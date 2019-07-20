<template>
    <tbody>
        <tr v-for="(row, indx) in rows">
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
            body: Object
        },
        data(){
          return {
              rows: this.body.rows
          }
        }
    }
</script>

<style scoped>

</style>