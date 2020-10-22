<template>
	<div class="app">
		<Navbar />
		<div class="weatherImageBg" alt="New York City Background" />
		<SearchCity
			:city="city"
			v-on:changeCity="changeCity($event)"
			v-on:searchWeather="searchWeather()"
		/>
		<Model :weatherData="weatherData" />
	</div>
</template>

<script>
import Navbar from "./components/Navbar.vue";
import SearchCity from "./components/SearchCity.vue";
import Model from "./components/Model.vue";

const KEY_OPENWEATHERMAP = process.env.VUE_APP_KEY_OPENWEATHERMAP;

export default {
	name: "App",
	components: {
		Navbar,
		SearchCity,
		Model
	},
	data: () => ({
		city: "",
		weatherData: {
			city: "Empty",
			temperature: "0",
			icon: "http://openweathermap.org/img/wn/10n@2x.png"
		}
	}),
	methods: {
		changeCity: function(message) {
			console.log(message.normalize("NFD").replace(/[\u0300-\u036f]/g, ""));
			return (this.city = message);
		},
		searchWeather: async function() {
			try {
				const response = await fetch(
					`http://api.openweathermap.org/data/2.5/weather?q=${this.city}&appid=${KEY_OPENWEATHERMAP}&units=metric`
				);

				if (response.status == 200) {
					const data = await response.json();

					this.weatherData = {
						city: data.name,
						temperature: Math.round(data.main.temp),
						icon: `http://openweathermap.org/img/wn/${data.weather[0].icon}@2x.png`
					};
				} else {
					this.weatherData = {
						...this.weatherData,
						city: "Ciudad no encontrada"
					};
				}
			} catch (error) {
				console.log("Error fetch: ", error);
			}
		}
	}
};
</script>

<style>
* {
	box-sizing: border-box;
}

.app {
	position: fixed;
	padding: 0;
	margin: 0;
	top: 0;
	left: 0;
	height: 100%;
	width: 100%;
	background-color: rgba(8, 16, 23);
	background-position: center;
	background-repeat: no-repeat;
	background-size: 100% 60%;
}

.weatherImageBg {
	background-image: url("https://i1.wp.com/conocenewyork.com/wp-content/uploads/2016/09/empire2.jpg?zoom=2&resize=920%2C425");
	background-position: center;
	filter: brightness(70%);
	position: absolute;
	height: 60%;
	width: 100%;
	z-index: -1;
}
</style>
