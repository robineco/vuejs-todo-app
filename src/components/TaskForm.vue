<template>
    <div id="form">
        <form>
            <div id="wrapper">
                <div id="wrapper-form">
                    <div id="wrapper-input">
                        <div id="field-name">
                            <md-field>
                                <label>Task Name</label>
                                <md-input v-model="task.name"></md-input>
                            </md-field>
                        </div>
                    </div>
                    <div id="wrapper-input">
                        <div id="field-content">
                            <md-field>
                                <label>Despcription</label>
                                <md-input v-model="task.content"></md-input>
                            </md-field>
                        </div>
                    </div>
                </div>  

                <div id="wrapper-button">
                    <md-button class="md-fab md-mini md-primary" @click="handleSubmit">
                        <md-icon>add</md-icon>
                    </md-button>
                </div>
            </div>
        </form>
    </div>
</template>

<script>
export default {
    name: "task-form",
    data() {
        return {
            task: {
                name: "",
                content: "",
            }
        }
    },
    methods: {
        handleSubmit() {
            if(this.task.name === "") {
                return;
            }
            this.$emit("add:task", this.task)
            this.task.name = "";
            this.task.content = "";
        }
    }
}
</script>

<style scoped>
#form {
    margin-top: 3rem;
}
#wrapper-form {
    display: inline-block;
    text-align: center;
}
#wrapper-input {
    text-align: center;
}
#field-name {
    display: inline-block;
    width: 30rem;

}
#field-content {
    display: inline-block;
    width: 30rem;
}
#wrapper-button {
    display: inline-block;
    vertical-align: middle;
}
</style>