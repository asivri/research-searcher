<template>
    <ul>
        PaperList
        <PaperListItem></PaperListItem>
    </ul>
</template>

<script>
    import PaperListItem from "./PaperListItem";

    export default {
        name: 'PaperList',
        components: {
            PaperListItem
        }
    }
</script>