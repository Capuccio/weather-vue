<template>
	<div class="navbar">
		<div class="navbar__logo">
			<img src="./../assets/clouds.svg" alt="Logo Company" />
		</div>

		<div class="navbar__options">
			<div class="navbar__item">Home</div>
			<div class="navbar__item">News</div>
			<div class="navbar__item">Live cameras</div>
			<div class="navbar__item">Photos</div>
			<div class="navbar__item">Contact</div>
		</div>
	</div>
</template>

<script>
export default {
	name: 'Navbar',
}
</script>

<style scoped>
.navbar {
	color: white;
	overflow: hidden;
	padding: 2% 4%;
}

.navbar__logo {
	display: block;
	float: left;
	width: 100px;
	height: 100px;
	padding: 0 0.6%;
}

.navbar__options {
	margin: 1.2% auto;
	text-align: center;
	float: right;
	overflow: hidden;
	width: 50%;
}

.navbar__item {
	letter-spacing: 1px;
	font-weight: 530;
	float: left;
	padding: 1% 3%;
	margin-left: 2%;
	border: 2px solid transparent;
	border-radius: 20px;
	transition: 0.2s;
	font-size: 16px;
}

.navbar__item:hover {
	cursor: pointer;
	color: rgb(100, 113, 227);
	border: 2px solid rgb(100, 113, 227);
}
</style>
