<template>
	<div class="model">
		<div class="model__city">{{weatherData.city}}</div>
		<div class="model__temperature">
			{{weatherData.temperature}}°C
			<img
				:src="weatherData.icon"
				alt="Weather icon"
				class="model__temperature__icon"
			/>
		</div>
	</div>
</template>

<script>
export default {
	name: "Model",
	props: {
		weatherData: Object
	}
};
</script>

<style>
.model {
	width: 50%;
	margin: 3% auto;
	height: 50%;
	color: white;
	background-color: rgba(16, 32, 46);
	border-radius: 10px;
}

.model__city {
	border-radius: 10px 10px 0 0;
	padding: 1% 3%;
	font-size: 17px;
	color: rgba(196, 196, 196);
	background-color: rgba(23, 46, 66);
}

.model__temperature {
	display: flex;
	font-size: 1in;
	font-weight: bold;
	text-align: center;
	margin: 9% 0;
	align-items: center;
	justify-content: center;
}
</style>
