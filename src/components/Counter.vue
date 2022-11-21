<template>
    <button v-on:click="count++">He sido pulsado {{count}} veces</button>
</template>

<script>
export default {
    data(){
        return{
            count: 0
        }
    }
}
</script>

<style>

</style>