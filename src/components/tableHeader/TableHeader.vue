<template>
    <thead>
        <tr>
            <th scope="col" v-for="name in names">{{name}}</th>
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