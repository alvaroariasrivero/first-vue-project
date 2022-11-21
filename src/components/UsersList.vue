<template>
    <div>
        <button v-on:click="addUSer">Añadir Usuario</button>
        <div>
            <div v-for="userId in users" :key="userId">
                <user-item :id="userId" @delete="onDeleteClicked"/>
            </div>
        </div>
    </div>
</template>

<script>
import UserItem from './UserItem.vue'
export default {
    name: 'UsersList',
    components: { UserItem },
    data(){
        return{
            users: [],
            nextId: 0
        }
    },
    methods: {
        addUSer(){
            this.users.push(this.nextId++);
        },
        onDeleteClicked(userId){
            this.users.splice(this.users.indexOf(userId), 1);
        }
    }
    
}
</script>