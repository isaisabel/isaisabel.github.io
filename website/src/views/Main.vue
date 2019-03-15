<template>
    <div class="gutter">
        <!-- carosel -->
        <div v-for="document in documents" v-bind:key="document.id" class="carosel-cell">
            <DocumentWrapper v-bind:documentComponent="document.component"></DocumentWrapper>
        </div>
    </div>
</template>

<script>
import LipsumDoc from "@/documents/LipsumDoc";
import AboutMeDoc from "@/documents/AboutMeDoc";
import DocumentWrapper from "@/components/DocumentWrapper";
export default {
    name: 'Main',
    props: {},
    components: {DocumentWrapper},
    data() { return {
        documents: [
            {
                "id": "lipsum",
                "component": LipsumDoc
            },
            {
                "id": "aboutme",
                "component": AboutMeDoc
            },
        ]
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
    .gutter { 
        background: color(gutter);
        // @extend .centering;
    }
    .carosel-cell {
        display: flex;
    }
</style>