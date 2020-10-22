<template>
	<div class="search">
		<input
			type="text"
			class="search__input"
			:value="city"
			placeholder="Find your location..."
			@input="changeCity"
			@keyup.enter="searchWeather"
		/>
		<button class="search__button" v-on:click="searchWeather">Find</button>
	</div>
</template>

<script>
export default {
	name: "SearchCity",
	props: {
		city: String,
		search: Function
	},
	methods: {
		changeCity: function(event) {
			this.message = event.target.value;
			this.$emit("changeCity", this.message);
		},
		searchWeather: function() {
			this.$emit('searchWeather', '');
		}
	}
};
</script>

<style>
.search {
	width: 70%;
	margin: 4% auto;
	text-align: center;
}

.search__input {
	width: 95%;
	padding: 20px;
	color: white;
	background-color: rgb(8, 16, 23);
	border: none;
	border-radius: 50px;
}

.search__button {
	margin-left: -6.9%;
	cursor: pointer;
	border: none;
	border-radius: 50px;
	padding: 20px;
	color: white;
	background-color: rgb(66, 135, 245);
}

.search__input:focus,
.search__button:focus,
.search__button:active {
	outline: none;
}

.search__button:active {
	background-color: rgb(50, 101, 184);
}
</style>
