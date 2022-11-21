<template>
    <div>
        <input type="number" v-model="number">
        <transition name="fade">
            <p v-if="showMessage"><slot></slot>{{romanized}}</p>
        </transition>
    </div>
</template>

<script>
export default {
    name: 'RomanCounter',
    data(){
        return{
            number: 0
        }
    },
    watch:{
        number(newValue){
            console.log('valor: ', newValue);
        }
    },
    computed: {
        romanized(){
            let num = this.number;
            let decimalValue = [1000, 900, 500, 400, 100, 90, 50, 40, 10, 9, 5, 4, 1];
            let romanNumeral = ['M', 'CM', 'D', 'CD', 'C', 'XC', 'L', 'XL', 'X', 'IX', 'V', 'IV', 'I'];
            let romanized = "";
            for(let i = 0; i < decimalValue.length; i++){
                while(decimalValue[i] <= num){
                    romanized += romanNumeral[i];
                    num -= decimalValue[i];
                }
            }
            return romanized || "Escribe un número";
        },
        showMessage(){
            return this.number >= 0;
        }
    }
}
</script>

<style scoped>
    .fade-enter-active,
    .fade-enter-leave{
        transition: 0.5s;
    }
    .fade-enter,
    .fade-leave-to{
        opacity: 0;
    }
</style>