<template>
<div id="progressbar">
    <div :style="rectangle" id="todo" v-for="index in progress.todo" :key="index" />
    <div :style="rectangle" id="completed" v-for="index in progress.completed" :key="index" />

</div>
</template>

<script>
export default {
    name: "progress-bar",
    props: {
        progress: Object
    },
    computed: {
        rectangle() {
            return {
                height: "20px",
                width: `${100 / (this.progress.todo + this.progress.completed)}%`
            }
        }
    }
}
</script>

<style scoped>
#progressbar {
 width: 100%;
}
#todo {
    display: inline-block;
    background-color: darkorange;
    border: 1px solid black;
}
#completed {
    display: inline-block;
    background-color: darkgreen;
    border: 1px solid black;
}
</style>