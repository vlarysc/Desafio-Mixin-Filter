<template>
	<div id="app">
		<h1>Filtros & Mixins (Desafio)</h1>
		<!-- Exercício 1 -->
		<!-- Construir um filtro local que troca espaços por vírgula -->
		<p> {{ frase | espacoPorVirgula }} </p>
		
		<!-- Exercício 2 -->
		<!-- Filtro global que conta o tamanho de cada palavra e adiciona o 
			valor na string final -->
		<!-- "Pedro é legal" => "Pedro (5) é (1) legal (5)" -->
		<p> {{ frase | contar-palavras }} </p>

		<!-- Exercício 3 -->
		<!-- Implementar os exercicios 1 e 2 com propriedade computada -->
		<p> {{ fraseComVirgulas }} </p>
		<p> {{ fraseComTamanho }} </p>

		<!-- Exercício 4 -->
		<!-- Compartilhe a propriedade computada via mixin -->
	</div>
</template>

<script>
import frasesMixin from './frasesMixin'
export default {
	data() {
		return {
			frase: 'O mundo é grande.',
		}
	},
	filters: {
		espacoPorVirgula(valor) {
			return valor.replace(/\s/g, ',')
		}
	},
	computed: {
		fraseComVirgulas() {
			return this.frase.replace(/\s/g, ',')
		},
		fraseComTamanho() {
			return this.frase.split(' ').map(p => `${p} (${p.length})`).join(' ')
		},
	}
	
}
</script>

<style>
#app {
	font-family: 'Avenir', Helvetica, Arial, sans-serif;
	-webkit-font-smoothing: antialiased;
	-moz-osx-font-smoothing: grayscale;
	text-align: center;
	color: #2c3e50;
	margin-top: 60px;
	font-size: 2.5rem;
}
</style>
