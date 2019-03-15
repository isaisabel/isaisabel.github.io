<template>
    <div class="documentWrapper">
        <div v-bind:is="documentComponent"></div>
    </div>

</template>

<script>
export default {
    name: 'DocumentWrapper',
    props: ["documentComponent"],
    data() { return {

    }},
    computed: {},
    watch: {},
    mounted: function() {},
    methods: {}
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style lang="scss">
    @import "@/style/globals.scss";
    .documentWrapper {
        width: 6in;
        background: color(page);
        color: on-color(page);
        padding: 0.5in 1in;
        margin: 25px;
        transition: all ease 0.35s;
        &:hover { 
            box-shadow: 7px 10px 10px 0px rgba(0,0,0,0.2);
            transform: translate(-2px, -3px);
        }
        white-space: normal;
        // flex-grow: 0;
    }
</style>