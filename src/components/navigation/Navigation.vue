<template>
    <div class="container-fluid">
        <nav class="navbar navbar-light bg-light row">
            <div v-on:click="onButtonClick" class="row col-lg-8 col-sm-8 cl-12">
                <button v-for="rule in navigation" v-bind:id="rule" type="button" class="btn btn-success m-1">
                    {{`Sort by: ${rule}`}}
                </button>
            </div>
            <div class="col-lg-4 col-sm-4 col-12">
                <input v-on:input="onSearchInput" class="form-control m-1 col" type="search" placeholder="Search" aria-label="Search">
            </div>
        </nav>
    </div>
</template>

<script>
    export default {
        name: "Navigation",
        props: {
            navigation: Array
        },
        methods: {
            onButtonClick(event){
                let id = event.target.getAttribute ("id");

                if(this.sortRules.includes(id)){
                    id = id.toLowerCase();
                    this.$emit("onButtonClick", {rule: id});
                }
            },
            onSearchInput(event){
                const {target: {value}} = event;
                this.$emit("onSearchInput", {value});
            }
        }
    }
</script>

<style scoped>

</style>