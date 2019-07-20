<template>
    <div class="container-fluid">
        <nav class="navbar navbar-light bg-light row">
            <form class="form-inline">
                <input class="form-control mr-sm-2" type="search" placeholder="Search" aria-label="Search">
            </form>
        </nav>
    </div>
</template>

<script>
    export default {
        name: "Navigation",
        props: {
            navigation: Object
        },
        data(){
            return {
                sortRules: this.navigation.sortRules
            }
        }
    }
</script>

<style scoped>

</style>