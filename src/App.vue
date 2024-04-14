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
			<div class="user_data">
				<p class="user_name user_value">Моисеев Михаил Сергеевич</p>
				<p class="user_birth_date user_value">13.08.1980</p>
				<p class="user_license user_value">Таб №: ГОКИ 0000</p>
				<p class="user_position user_value">
					Электрослесарь (слесарь дежурный по ремонту оборудования) 1
					разряда
				</p>
			</div>
			<div class="study_pages">
				<div class="breafing study_pages_size">1</div>
				<div class="tests_done study_pages_size">2</div>
				<div class="pre-shift_exam study_pages_size">3</div>
				<div class="certification_through study_pages_size">4</div>
			</div>
		</div>
		<div class="main">
			<div class="amicum_logo"></div>
			<div class="main_pages">
				<div class="main_pages_size">
					<p>Начать работу</p>
					<img src="" alt="" />
				</div>
				<div class="main_pages_size">
					<p>Уведомления</p>
					<img src="" alt="" />
				</div>
				<div class="main_pages_size">
					<p>Обучение</p>
					<img src="" alt="" />
				</div>
				<div class="main_pages_size">
					<p>Достижения</p>
					<img src="" alt="" />
				</div>
			</div>
		</div>
	</div>
</template>

<style scoped>
@import url('https://fonts.googleapis.com/css2?family=Montserrat:ital,wght@0,100..900;1,100..900&display=swap');

.main_pages_size {
	width: 390px;
	height: 300px;
	background-color: #ef7f1a;
}

.main_pages {
	display: flex;
	flex-wrap: wrap;
	justify-content: center;
	align-items: center;
	margin-top: 280px;
	gap: 100px;
	@media only screen and (min-width: 2032px) {
		margin-left: 100px;
		margin-right: 100px;
	}
}

.amicum_logo {
	background-image: url(/src/images/AMICUM-logo.png);
	width: 217px;
	height: 77px;
	margin: 20px 20px 0 0;
	position: fixed;
	right: 0;
}

.study_pages {
	display: flex;
	flex-wrap: wrap;
	margin-top: 58px;
	justify-content: center;
	align-items: center;
}

.study_pages_size {
	width: 281px;
	height: 260px;
	background-color: #586c92;
	box-shadow: 0px 6px 10px 0px rgba(0, 0, 0, 0.45);
	margin-bottom: 20px;
	border-radius: 4px;
}

.study_pages_size:nth-child(odd) {
	margin-right: 20px;
}

.container {
	display: flex;
	background-color: #586c92;
}

.menu {
	width: 662px;
	position: sticky;
	top: 0;
	background-color: #353d54;
	border-top-right-radius: 16px;
	border-bottom-right-radius: 16px;
	box-shadow: 6px 0px 7px rgba(0, 0, 0, 0.3);
	display: flex;
	flex-direction: column;
	@media only screen and (min-height: 1067px) {
		height: 100vh;
	}
}

.main {
	width: calc(100vw - 662px);
	display: flex;
	flex-direction: column;
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
	margin: 88px 40px 82px 0;
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

.user_data {
	color: #ffffff;
	background-color: #586c92;
	max-width: 582px;
	align-self: center;
	padding: 10px 10px 0 15px;
	border-radius: 4px;
	box-shadow: 0px 6px 10px 0px rgba(0, 0, 0, 0.45);
	display: flex;
	flex-direction: column;
	flex-wrap: wrap;
}

.user_value {
	font-family: 'Montserrat', sans-serif;
	margin-bottom: 10px;
}

.user_name {
	font-weight: 700;
	font-size: 32px;
}

.user_birth_date {
	font-weight: 600;
	font-size: 24px;
}

.user_license,
.user_position {
	font-weight: 600;
	font-size: 16px;
}
</style>
