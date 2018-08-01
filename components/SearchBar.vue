<template>

    <input @input="onSearchBar" /> <!-- @ or v-on used for listening DOM elements. -->

</template>

<script>
    export default {
        methods: {
            onSearchBar: function(event)
            {
                this.$emit('newSearch', event.target.value);
            }
        }
    }
</script>


<style>
</style>