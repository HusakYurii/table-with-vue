<template>
    <div class="container-fluid">
        <nav class="navbar navbar-light bg-light row">
            <div v-on:click="onButtonClick" class="row col-lg-8 col-sm-8 cl-12">
                <button v-for="rule in sortRules" v-bind:id="rule" type="button" class="btn btn-success m-1">{{`Sort by: ${rule}`}}</button>
            </div>
            <form class="form-inline col-lg-4 col-sm-4 col-12">
                <input v-on:input="onSearchInput" class="form-control m-1 col" type="search" placeholder="Search" aria-label="Search">
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
                sortStates: this.navigation.sortStates,
                isBtnDataSet: false,
                firstBtn: null,
                secondBtn: null
            }
        },
        methods: {
            onButtonClick(event){
                const { id, state } = this.defineBtn(event.target);
                this.$emit("onButtonClick", {id, state});
            },
            onSearchInput(event){
                const {target: {value}} = event;
                this.$emit("onSearchInput", {value});
            },
            defineBtn(btn){
                !this.firstBtn && this.setBtn("firstBtn", btn);
                !this.secondBtn && (btn !== this.firstBtn.origin) && this.setBtn("secondBtn", btn);

                return (btn === this.firstBtn.origin) ? this.firstBtn : this.secondBtn;
            },
            setBtn(type, btn){
                this[type] = {
                    state: this.sortStates.smToLg,
                    id: btn.getAttribute("id"),
                    origin: btn
                }
            }
        }
    }
</script>

<style scoped>

</style>