<template>
    <div>
        <div v-for="tarea in tareas" :key="tarea.id">
            <div v-if="!tarea.Done">
                <h3>{{tarea.Tarea}}</h3>
                <h5>Asignada a: {{tarea.Asignada}}</h5>
                <p>Descripcion: {{tarea.Descripcion}}</p>
                <button v-on:click="function deleteTask(){tarea.Done = true}">Done</button>
            </div>
        </div>
    </div>
</template>

<script>
export default {
    name: 'TaskCard',
    props:["tareas", 'deleteTask']
}
</script>

<style scoped>

</style>