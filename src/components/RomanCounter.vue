<template>
    <div>
        <input type="number" v-model="number">
        <p>Equivalente romano: {{romanized}}</p>
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
        }
    }
}
</script>