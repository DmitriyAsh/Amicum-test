<script setup>
import moment from 'moment';
import { ref, computed } from 'vue';

const date = ref(setTime());

function setTime() {
	return moment().format('DD.MM.YYYY HH:mm');
}

setInterval(() => (date.value = setTime()), 1000 * 30);

const userData = ref({
	userName: 'Моисеев Михаил Сергеевич',
	birthDate: '13.08.1980',
	userLicense: 'Таб №: ГОКИ 0000',
	userPosition:
		'Электрослесарь (слесарь дежурный по ремонту оборудования) 1 разряда',
});

const colors = {
	true: '#B2D63C',
	false: '#EF7F1A',
};

const totalTests = 500;
const testsDone = 108;
const progressOfTests = computed(() => (testsDone / totalTests) * 100);
const totalDays = 365;
const daysUntilExam = 30;
const daysUntilExamProgressBar = computed(
	() => (daysUntilExam / totalDays) * 100
);
const colorByProgress = computed(() => {
	if (daysUntilExam <= 30) {
		return '#EF7F1A';
	}
	return '#B2D63C';
});
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
				<p class="user_name user_value">{{ userData.userName }}</p>
				<p class="user_birth_date user_value">
					{{ userData.birthDate }}
				</p>
				<p class="user_license user_value">
					{{ userData.userLicense }}
				</p>
				<p class="user_position user_value">
					{{ userData.userPosition }}
				</p>
			</div>
			<div class="study_pages">
				<button class="study_pages_size">
					<p class="study_pages_text">Инструктаж</p>
					<svg
						width="145"
						height="145"
						viewBox="0 0 250 250"
						class="circular-progress"
						style="--progress: 100"
					>
						<circle class="bg"></circle>
						<circle
							class="fg"
							:style="`--color: ${colors.true}`"
						></circle>
					</svg>
					<img
						src="/src/images/breafing.png"
						alt="#"
						class="breafing"
					/>
				</button>
				<button class="study_pages_size">
					<p class="study_pages_text">Предсменный инструктаж</p>
					<svg
						width="145"
						height="145"
						viewBox="0 0 250 250"
						class="circular-progress"
						style="--progress: 100"
					>
						<circle class="bg"></circle>
						<circle
							class="fg"
							:style="`--color: ${colors.false}`"
						></circle>
					</svg>
					<img
						src="/src/images/pre-shift-exam.png"
						alt="#"
						class="pre_shift_exam"
					/>
				</button>
				<button class="study_pages_size">
					<p class="study_pages_text">Тестов выполнено&shy;</p>
					<svg
						width="145"
						height="145"
						viewBox="0 0 250 250"
						class="circular-progress"
						:style="`--progress: ${progressOfTests}`"
					>
						<circle class="bg"></circle>
						<circle
							class="fg"
							:style="`--color: ${colors.true}`"
						></circle>
					</svg>
					<p class="tests_done">{{ testsDone }}</p>
				</button>
				<button class="study_pages_size">
					<p class="study_pages_text">Аттестация через&shy;</p>
					<svg
						width="145"
						height="145"
						viewBox="0 0 250 250"
						class="circular-progress"
						:style="`--progress: ${daysUntilExamProgressBar}`"
					>
						<circle class="bg"></circle>
						<circle
							class="fg"
							:style="`--color: ${colorByProgress}`"
						></circle>
					</svg>
					<p class="days_unitl_exam">
						<span>{{ daysUntilExam }}</span>
						<span class="text_days">дней</span>
					</p>
				</button>
			</div>
		</div>
		<div class="main">
			<div class="amicum_logo"></div>
			<div class="main_pages">
				<button class="main_pages_size">
					<p class="main_pages_text">Начать работу</p>
					<img src="/src/images/bumper.png" alt="bumper" />
				</button>
				<button class="main_pages_size notes_parent">
					<p class="main_pages_text">Уведомления</p>
					<img src="/src/images/notes.png" alt="" />
				</button>
				<button class="main_pages_size">
					<p class="main_pages_text">Обучение</p>
					<img src="/src/images/study.png" alt="" />
				</button>
				<button class="main_pages_size">
					<p class="main_pages_text">Достижения</p>
					<img src="/src/images/achievements.png" alt="" />
				</button>
			</div>
		</div>
	</div>
</template>

<style scoped>
@import url('https://fonts.googleapis.com/css2?family=Montserrat:ital,wght@0,100..900;1,100..900&display=swap');

.circular-progress {
	--size: 250px;
	--half-size: calc(var(--size) / 2);
	--stroke-width: 20px;
	--radius: calc((var(--size) - var(--stroke-width)) / 2);
	--circumference: calc(var(--radius) * pi * 2);
	--dash: calc((var(--progress) * var(--circumference)) / 100);
}

.circular-progress circle {
	cx: var(--half-size);
	cy: var(--half-size);
	r: var(--radius);
	stroke-width: var(--stroke-width);
	fill: none;
	stroke-linecap: round;
}

.circular-progress circle.bg {
	stroke: #353d54;
}

.circular-progress circle.fg {
	transform: rotate(-90deg);
	transform-origin: var(--half-size) var(--half-size);
	stroke-dasharray: var(--dash) calc(var(--circumference) - var(--dash));
	transition: stroke-dasharray 0.3s linear 0s;
	stroke: var(--color);
}

.notes_parent {
	position: relative;
}

.notes_parent::before {
	position: absolute;
	top: -30px;
	right: -30px;
	content: '2';
	width: 60px;
	height: 60px;
	border-radius: 50%;
	background-color: #acd91b;
	display: flex;
	justify-content: center;
	align-items: center;
	font-family: 'Montserrat', sans-serif;
	font-weight: 600;
	font-size: 32px;
}

.main_pages_text {
	margin-bottom: 40px;
	font-family: 'Montserrat', sans-serif;
	font-weight: 600;
	font-size: 36px;
	color: #ffffff;
}

.main_pages_size {
	width: 390px;
	height: 300px;
	background-color: #ef7f1a;
	border-radius: 4px;
	box-shadow: 0px 6px 10px 0px rgba(0, 0, 0, 0.45);
	display: flex;
	flex-direction: column;
	align-items: center;
	border: none;
	cursor: pointer;
	padding-top: 40px;
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
	text-align: center;
}

.study_pages_text {
	font-family: 'Montserrat', sans-serif;
	font-weight: 700;
	font-size: 20px;
	color: #ffffff;
}

.study_pages_size {
	width: 281px;
	height: 260px;
	background-color: #586c92;
	box-shadow: 0px 6px 10px 0px rgba(0, 0, 0, 0.45);
	margin-bottom: 20px;
	border-radius: 4px;
	display: flex;
	flex-direction: column;
	justify-content: center;
	align-items: center;
	gap: 13px;
	border: none;
	cursor: pointer;
	position: relative;
}

.breafing {
	position: absolute;
	bottom: 60px;
	right: 90px;
}

.pre_shift_exam {
	position: absolute;
	bottom: 60px;
	right: 97px;
}

.tests_done {
	position: absolute;
	font-family: 'Montserrat', sans-serif;
	font-weight: 600;
	font-size: 45px;
	color: #ffffff;
	bottom: 75px;
}

.days_unitl_exam {
	position: absolute;
	font-family: 'Montserrat', sans-serif;
	font-weight: 600;
	font-size: 40px;
	color: #ffffff;
	bottom: 70px;
	display: flex;
	flex-direction: column;
}

.text_days {
	font-size: 20px;
	margin-top: -5px;
}

.study_pages_size:nth-child(odd) {
	margin-right: 20px;
}

.study_pages_size:nth-child(1) {
	gap: 30px;
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
