<template>
    <h1>{{ this.progress.completed }} / {{ this.progress.todo + this.progress.completed }}</h1>
</template>
<script>
export default {
    name: "progress-indicator",
    props: {
        progress: Object,
    }
}
</script>

<style scoped>

</style>