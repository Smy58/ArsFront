<template>
	<div class="finance-popup">
		<div class="finance-popup__bg"></div>
		<div class="finance-popup__content">
			<img :src="closeImg" alt="close" class="finance-popup__close" @click="closePopup">
			<form action="" class="finance-popup__form form-popup">
				<div class="form-popup__field form-popup__field_big">
					<p class="form-popup__label">Тип и дата</p>
					<select :value="fynType" @input="clicked">
						<option
							v-for="option in fynTypes"
							:key="option.id"
							:value="option.value"
							>
							{{ option.value }}
						</option>
					</select>
					<input v-model="date" type="date" class="form-popup__input">
				</div>
				<div class="form-popup__field">
					<p class="form-popup__label">Сумма</p>
					<input v-model="price" type="number" class="form-popup__input">
				</div>
				<div class="form-popup__field">
					<p class="form-popup__label">Плательщик</p>
					<input v-model="author" type="text" class="form-popup__input">
				</div>
				<div class="form-popup__field">
					<p class="form-popup__label">Комментарий</p>
					<input v-model="describe" type="text" class="form-popup__input">
				</div>
				<div class="form-popup__btns">
					<button class="form-popup__btn form-popup__btn_cancel" @click="closePopup">Отмена</button>
					<button class="form-popup__btn form-popup__btn_add" @click.prevent="logger">Сохранить
						<img :src="okImg" alt="ok">
					</button>
				</div>
			</form>
		</div>
	</div>
</template>

<script>
const fynTypes = [{
	id: 1,
	value: 'Доход'
}, 
{
	id: 2,
	value: 'Расход'
}, 
{
	id: 3,
	value: 'Выплата ЗП'
}, 
{
	id: 4,
	value: 'Возврат Средств'
}]

import okImg from '~/assets/finance/ok.svg'
import closeImg from '~/assets/finance/close.svg'

export default {
	data() {
		return {
			fynType: 'Доход',
			fynTypes: fynTypes,
			date: '',
			price: 0,
			author: '',
			describe: '',
			okImg: okImg,
			closeImg: closeImg,

		}
	},
	setup() {
		
	},
	methods: {
		logger() {
			const item = {
				fynType: this.fynType,
				date: this.date,
				price: this.price,
				author: this.author,
				describe: this.describe
			}
			console.log(item);
		},
		clicked($event) {
			this.fynType = $event.target.value
		}
	},
	props: {
		closePopup: Function
	}
}
</script>

<style lang="scss">
.finance-popup {
	position: fixed;
	width: 100%;
	height: 100%;
	top: 0;
	left: 0;

	&__close {
		position: absolute;
		top: 10px;
		right: 10px;

		cursor: pointer;
	}


	&__bg {
		position: absolute;
		top: 0;
		left: 0;
		width: 100%;
		height: 100%;

		background: #00000020;
	}

	&__content {
		position: absolute;
		top: 50%;
		left: 50%;
		transform: translate(-50%, -50%);
		width: 602px;
		height: 340px;

		background: #fff;
		border-radius: 7px;

		padding: 33px;
		padding-top: 48px;
		box-sizing: border-box;
		
	}

	&__form {
		
	}
	
	.form-popup {
		display: flex;
		flex-direction: column;
		align-items: center;
		gap: 23px;

		&__field {
			width: 100%;
			display: grid;
			grid-template-columns: 2fr 6fr;
			gap: 13px;

			&_big {
				grid-template-columns: 2fr 3fr 3fr;	
			}
		}

		

		&__label {
			margin: 0;

			font-family: Gilroy;
			font-size: 16px;
			line-height: 30px;
			font-weight: 400;
		}

		&__input {
			height: 30px;
			border: #B4B4B4 solid 1px;

			color: #646464;

			outline: none;

			font-family: Gilroy;
			font-size: 16px;
			padding-left: 5px;
			padding-right: 5px;

			&::-webkit-inner-spin-button,
			&::-webkit-outer-spin-button {
				-webkit-appearance: none;
				margin: 0;
			}
		}

		&__btns {

			display: flex;
			flex-direction: row;
			align-self: flex-end;
		}

		&__btn {
			background: #5192B7;
			padding: 11px;
			font-family: Gilroy;
			font-size: 16px;
			line-height: 16px;
			font-weight: 400;
			color: white;

			display: flex;
			flex-direction: row;
			align-items: center;
			gap: 4px;

			box-sizing: border-box;
			border: none;
			outline: none;
			border-radius: 5px;

			&_cancel {

				background: none;
				color: #5B5B5B;
			}

			&_add {
			}
		}
	}
}

</style>