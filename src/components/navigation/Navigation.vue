<template>
    <div class="container-fluid">
        <nav class="navbar navbar-light bg-light row">
            <div v-on:click="onButtonClick" class="row col-lg-8 col-sm-8 cl-12">
                <button v-for="rule in sortRules" v-bind:id="rule" type="button" class="btn btn-success m-1">{{`Sort by: ${rule}`}}</button>
            </div>
            <form class="form-inline col-lg-4 col-sm-4 col-12">
                <input v-on:input="onInputData" class="form-control m-1 col" type="search" placeholder="Search" aria-label="Search">
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
                sortRules: this.navigation.sortRules,
            }
        },
        methods: {
            onButtonClick(event){

            },
            onInputData(event){

            }
        }
    }
</script>

<style scoped>

</style>