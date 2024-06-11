<script setup>
import { reactive } from 'vue';

const estado = reactive({
    num1: 0,
    num2: 0,
    operacao: 'soma',
    resultado: null,
})

function calcularResultado() {
    switch (estado.operacao) {
        case 'soma':
            estado.resultado = soma();
            break;
        case 'subtracao':
            estado.resultado = subtracao();
            break;
        case 'multiplicacao':
            estado.resultado = multiplicacao();
            break;
        case 'divisao':
            estado.resultado = divisão();
            break;
    }
}

function soma() {
    const { num1, num2 } = estado;
    return num1 + num2;
}

function subtracao() {
    const { num1, num2 } = estado;
    return num1 - num2;
}

function multiplicacao() {
    const { num1, num2 } = estado;
    return num1 * num2;
}

function divisão() {
    const { num1, num2 } = estado;
    if (num2 === 0) {
        alert("Denominador não pode ser 0")
        return null;
    }
    else {
        return num1 / num2;
    }
}

</script>

<template>
<div class="calculadora">
    <h1>Calculadora aritmética</h1>
    <br />
    <div class="form">
        <label>Primeiro número:</label>
        <input type="number" v-model="estado.num1" placeholder="Insira um número" class="form-control">
        <br />
        <label>Segundo número:</label>
        <input type="number" v-model="estado.num2" placeholder="Insira um número" class="form-control">
        <br />
        <label>Selecionar operação:</label>
        <select v-model="estado.operacao" @change="calcularResultado" class="form-select">
            <option value="soma">Soma</option>
            <option value="subtracao">Subtração</option>
            <option value="multiplicacao">Multiplicação</option>
            <option value="divisao">Divisão</option>
        </select>
        <br />
        <label>Resultado:</label>
        <input type="text" :value="estado.resultado" class="form-control" readonly>
    </div>
</div>

</template>

<style scoped>
.calculadora {
    display: flex;
    flex-direction: column;
    align-items: center;
    justify-content: center;
    height: 100vh;
}
</style>
