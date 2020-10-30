<template>
    <div id="task-table">
        


        <md-card md-with-hover id="card" v-for="task in tasks" :key="task.id">
            <md-ripple>
                <md-card-header>
                <div class="md-title">{{ task.name }}</div>
                </md-card-header>

                <md-card-content>
                    {{ task.content }}
                </md-card-content>

                <md-card-actions>
                    <md-button class="md-primary" @click="handleComplete(task.id)">Complete</md-button>
                </md-card-actions>
            </md-ripple>
        </md-card>
    </div>
</template>

<script>
export default {
    name: "task-table",
    props: {
        tasks: Array,
    },
    methods: {
        handleComplete(id) {
            this.$emit("remove:task", id)
        }
    }
}
</script>

<style scoped>
#task-table {
    margin-top: 2rem;
    display: inline-block;
}
#card {
    margin-bottom: 1rem;
}
</style>