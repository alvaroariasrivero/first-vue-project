<template>
    <div>
        <span>User {{id}}</span>
        <input type="text" name="name" v-model="name" placeholder="Nombre">
        <input type="text" name="surname" v-model="surname" placeholder="Apellidos">
        <button v-on:click="onDeleteClicked">X</button>
    </div>
</template>

<script>
export default {
    name : 'UserItem',
    props: {
        id: Number
    },
    data(){
        return{
            name: "",
            surname: ""
        }
    },
    methods:{
        onDeleteClicked(){
            this.$emit('delete', this.id)
        }
    }    
}
</script>