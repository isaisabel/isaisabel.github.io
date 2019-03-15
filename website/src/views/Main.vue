<template>
    <div ref="viewport" class="gutter viewport" v-bind:style="viewportPos">
        <!-- carosel -->
        <div v-for="(document, index) in documents" 
             v-bind:key="document.id" class="carosel-cell" 
             v-on:click="selectedIndex = index"
             v-bind:class="{selected: selectedIndex == index}">
            <DocumentWrapper v-bind:documentComponent="document.component"></DocumentWrapper>
        </div>
    </div>
</template>

<script>
import LipsumDoc from "@/documents/LipsumDoc";
import AboutMeDoc from "@/documents/AboutMeDoc";
import ThirdDoc from "@/documents/ThirdDoc";
import FourthDoc from "@/documents/FourthDoc";

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
            {
                "id": "thirddoc",
                "component": ThirdDoc
            },
            {
                "id": "fourthdoc",
                "component": FourthDoc
            },
        ],
        selectedIndex: 0,
        mounted: false
    }},
    computed: {
        viewportPos() {
            if (!this.mounted) return {}
            let viewportWidth = this.$el.offsetWidth;
            console.log(viewportWidth)
            let docWidth = viewportWidth / this.documents.length;
            let offset = (docWidth/2  -(this.selectedIndex * docWidth)) + "px"
            console.log(offset);
            return { "left": offset }
        }
    },
    watch: {},
    mounted: function() { this.mounted = true;},
    methods: {
        // viewportOffset() {
        //     // compute offset
        //     let dist = index - this.selectedIndex;
        //     let distStr =  (dist * 50 + 2) + "%"
        //     return {"left": distStr }
        // }
    }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style lang="scss">
    @import "@/style/globals.scss";
    .gutter { 
        background: color(gutter);
        // @extend .centering;
        // overflow-x: hidden;
    }
    .viewport {
        position: absolute;
        top: 0;
        overflow-x:hidden;
        white-space: nowrap;
        transition: all ease 0.6s;

    }
    .carosel-cell {
        display: inline-flex;
        // height: 100vh;
        // width: 75vw;
        // position: absolute;
        transition: all ease 0.2s;
        &.selected {
            z-index: 100;
        }
        &:not(.selected):not(:hover) {
            filter: blur(5px);
        }
    }
</style>