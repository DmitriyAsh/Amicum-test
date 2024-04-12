<script setup>
import moment from 'moment';
import { ref } from 'vue';

const date = ref(setTime());

function setTime() {
	return moment().format('DD.MM.YYYY HH:mm');
}

setInterval(() => (date.value = setTime()), 1000 * 60);
</script>

<template>
	<div class="container">
		<div class="menu">
			<div class="menu_head">
				<div class="date">{{ date }}</div>
				<button class="exit-btn">
					<span class="text-btn">Выход</span>
					<img src="/src/icons/exit-icon.svg" alt="#" />
				</button>
			</div>
			<label class="switch">
				<input type="checkbox" />
				<span class="slider"></span>
			</label>
		</div>
		<div class="main"></div>
	</div>
</template>

<style scoped>
@import url('https://fonts.googleapis.com/css2?family=Montserrat:ital,wght@0,100..900;1,100..900&display=swap');

.container {
	display: flex;
	background-color: #586c92;
}

.menu {
	width: 662px;
	height: 100vh;
	background-color: #353d54;
	border-top-right-radius: 16px;
	border-bottom-right-radius: 16px;
	box-shadow: 6px 0px 7px rgba(0, 0, 0, 0.3);
	display: flex;
	flex-direction: column;
}

.main {
	width: 100vw;
	height: 100vh;
}

.menu_head {
	display: flex;
	justify-content: space-between;
	margin-top: 30px;
	margin-left: 40px;
	margin-right: 33px;
	flex-wrap: wrap;
}

.date {
	font-family: 'Montserrat', sans-serif;
	font-weight: 700;
	font-size: 20px;
	color: #ffffff;
	width: 106px;
}

.exit-btn {
	display: flex;
	justify-content: center;
	align-items: center;
	background-color: transparent;
	border: none;
	cursor: pointer;
}

.text-btn {
	font-family: 'Montserrat', sans-serif;
	font-weight: 600;
	font-size: 24px;
	color: #ffffff;
	padding-right: 10px;
}

.switch {
	position: relative;
	display: inline-block;
	width: 76px;
	height: 20px;
	align-self: flex-end;
	margin-top: 88px;
	margin-right: 40px;
}

.switch input {
	display: none;
}

.slider {
	position: absolute;
	cursor: pointer;
	top: 0;
	left: 0;
	right: 0;
	bottom: 0;
	background-color: #586c92;
	-webkit-transition: 0.4s;
	transition: 0.4s;
	border-radius: 12px;
}

.slider:before {
	position: absolute;
	content: '';
	height: 71px;
	width: 71px;
	left: -25px;
	bottom: -21px;
	background-image: url(/src/icons/theme-switcher.svg);
	-webkit-transition: 0.5s;
	transition: 0.5s;
}

input:checked + .slider {
	background-color: #000;
}

input:checked + .slider:before {
	-webkit-transform: translateX(50px);
	-ms-transform: translateX(50px);
	transform: translateX(50px);
}
</style>
