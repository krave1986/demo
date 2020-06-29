<template>
	<div id="app">
		abc
	</div>
</template>

<script>
import * as d3 from "d3";

const data = [4, 8, 15, 16, 23, 42];
const width = 420;
const x = d3
	.scaleLinear()
	.domain([0, d3.max(data)])
	.range([0, width]);
const y = d3
	.scaleBand()
	.domain(d3.range(data.length))
	.range([0, 20 * data.length]);

export default {
	name: "App",
	data() {
		return {};
	},
	methods: {},
	mounted() {
		console.log(data);
		console.log(d3);
		console.log(x);
		console.log(y);
		console.log(width);

		const svg = d3
			.create("svg")
			.attr("width", width)
			.attr("height", y.range()[1])
			.attr("font-family", "sans-serif")
			.attr("font-size", "10")
			.attr("text-anchor", "end");

		const bar = svg
			.selectAll("g")
			.data(data)
			.join("g")
			.attr("transform", (d, i) => `translate(0,${y(i)})`);
	}
};
</script>

<style>
body {
	margin: 0;
}
</style>
