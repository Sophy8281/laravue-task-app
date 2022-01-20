<template>
    <div class="container">
        <div class="row justify-content-center">
            <div class="col-md-8">
                <div class="card">
                    <div class="card-header">Task List</div>

                    <div class="card-body">
                        <li v-for="task in tasks" :key="task.id">{{task.title}}</li>
                    </div>
                </div>
            </div>
        </div>
    </div>
</template>

<script>
    export default {
        data(){
            return{
                tasks: []
            }
        },

        created() {
            axios.get('./api/task')
            .then(response => this.tasks = response.data);

            Event.$on('taskCreated', (title) => {
                this.tasks.push(title);
            });

        }
    }
</script>
