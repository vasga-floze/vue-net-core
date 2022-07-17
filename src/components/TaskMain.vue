<template>
    <div>
        <h1 class="display 4 text-center pt-3">Listado de Tareas</h1>
        <hr>
        <div class="row">
            <div class="col-lg-8 offset-lg-2">
                <div class="card mt-4">
                    <div class="card-body">
                        <div class="input-group">
                            <input type="text" v-model="task" class="form-control form-control-lg" placeholder="Agregar tarea">
                            <div class="input-group-append">
                                <button v-on:click="addTask()" class="btn btn-success btn-lg">Agregar</button>
                            </div>
                        </div>
                        <br>
                        <h5 v-if="taskList.length == 0">No hay tareas planificadas</h5>
                        <ul class="list-group">
                            <li v-for="(task, index) of taskList" :key="index" class="list-group-item d-flex justify-content-between">
                                <span class="cursor">
                                    <i class="far fa-circle"></i>
                                </span>
                                {{task.name}}
                                <span class="text-danger cursor" v-on:click="deleteTask(index)">
                                    <i class="fas fa-trash-alt"></i>
                                </span>
                            </li>
                        </ul>
                    </div>
                </div>
            </div>
        </div>
    </div>
</template>

<script>
    export default {
        name: 'TaskMain',
        data() {
            return {
                task: '',
                taskList: []
            }
        },
        methods: {
            addTask(){
                const task = {
                    name: this.task,
                    state: false
                }
                this.taskList.push(task);
                this.task = '';
            },
            deleteTask(index){
                this.taskList.splice(index, 1)
            }
        }
    }
</script>

<style scoped>
.cursor {
    cursor: pointer;
}
</style>