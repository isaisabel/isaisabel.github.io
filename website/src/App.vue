<template>
    <div id="app">
        <router-view/>
    </div>
</template>
<script>
import DocumentWrapper from "@/components/DocumentWrapper";

export default {
    name: 'App',
    components: { DocumentWrapper },
    props: {},
}
</script>


<style lang="scss">
#app {
    @import "style/globals.scss";
    @include thefont;
}
</style>
