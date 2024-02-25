<template>
	<nav class="nav">
		<div class="nav__show" v-if="isNav">
			<img :src="arrow" alt="arrow" class="nav__arrow" v-on:click="hideNav">
			<img :src="logo" alt="logo" class="nav__logo">
			<ul class="nav__list">
				<li class="nav__block">
					<img :src="finance" alt="finance" class="nav__icon">
					<NuxtLink to="/finance" class="nav__link">Финансы</NuxtLink>
				</li>

				<li class="nav__block">
					<img :src="client" alt="client" class="nav__icon">
					<NuxtLink to="" class="nav__link">Клиенты</NuxtLink>
				</li>

				<li class="nav__block">
					<img :src="employe" alt="employe" class="nav__icon">
					<NuxtLink to="" class="nav__link">Сотрудники</NuxtLink>
				</li>

				<li class="nav__block">
					<img :src="finance" alt="employe" class="nav__icon">
					<NuxtLink to="/diagram" class="nav__link">Диаграмы</NuxtLink>
				</li>
			</ul>

			<div class="nav__account">
				<button class="nav__quit-btn">
					<img :src="quit" alt="quit" class="nav__quit-img">
				</button>
				<p class="nav__acc-name">{{ accName }}</p>
			</div>
		</div>
		<div class="nav__hide" v-else>
			<img :src="arrow" alt="arrow" class="nav__arrow nav__arrow_hide" v-on:click="hideNav">

		</div>
	</nav>
</template>

<script>
import logo from '~/assets/TheNavigation/Logo.svg'
import finance from '~/assets/TheNavigation/finance.svg'
import client from '~/assets/TheNavigation/client.svg'
import employe from '~/assets/TheNavigation/employe.svg'
import quit from '~/assets/TheNavigation/quit.svg'
import arrow from '~/assets/TheNavigation/arrow.svg'

export default {
	name: 'TheNavigation',
	data(){
		return {
			logo: logo,
			finance: finance,
			client: client,
			employe: employe,
			quit: quit,
			accName: 'Абдрахман У.',
			isNav: false,
			arrow: arrow,
		}
	},
	methods: {
		hideNav() {
			this.isNav = !this.isNav;
		}
	}
}
</script>

<style lang="scss">
	.nav {
		position: fixed;
		top: 0;
		left: 0;
		height: 100%;
		

		&__show {
			width: 192px;
			background: #fff;
			box-shadow: 0px 0px 10.100000381469727px 0px #0000001A;
			height: 100%;

			display: flex;
			flex-direction: column;
			align-items: center;

			padding: 19px 0;
			box-sizing: border-box;
		}

		&__hide {
			width: 30px;
			background: #fff;
			box-shadow: 0px 0px 10.100000381469727px 0px #0000001A;
			height: 100%;
		}

		&__arrow {
			position: absolute;
			right: 0;
			top: 50%;
			transform: translate(50%, -50%);

			&_hide {
				transform: translate(50%, -50%) rotate(180deg);

			}
		}


		&__logo {
			margin-bottom: 77px;
		}
		&__list {
			display: flex;
			flex-direction: column;
			align-items: center;

			list-style-type: none;

			margin: 0;
			padding: 0;

			width: 100%;
		}

		&__block {
			display: flex;
			flex-direction: row;
			align-items: center;

			width: 100%;
			border-top: 1px solid #CBCBCB;
			border-bottom: 1px solid #CBCBCB;

			box-sizing: border-box;

			padding: 6px 0;
			padding-left: 16px;
			gap: 22px;

			margin-bottom: -1px;

		}

		&__icon {

		}

		&__link {
			font-family: Gilroy;
			font-size: 16px;
			font-weight: 400;
			line-height: 19px;
			letter-spacing: 0em;
			text-align: left;

		}

		&__account {
			width: 100%;
			position: absolute;
			bottom: 0;
			left: 0;

			padding: 14px 0;
			padding-left: 15px;

			box-sizing: border-box;

			border-top: 1px solid #B4B4B4;


			display: flex;
			flex-direction: row;
			align-items: center;

		}

		&__quit-btn {

			padding: 0;
			background: none;
			border: none;
			outline: none;
			width: 33px;
			height: 33px;
		}

		&__quit-img {
			width: 33px;
			height: 33px;
		}

		&__acc-name {
			font-family: Gilroy;
			font-size: 16px;
			font-weight: 500;
			line-height: 19px;
			letter-spacing: 0em;
			text-align: center;

			color: #717171;

			margin: 0;


		}
	}





</style>