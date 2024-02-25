<template>
	<div class="finance">
		<div class="finance__btns">
			<button class="finance__add finance__btn"><img :src="add" alt="add" class="" @click="openPopup"></button>
			<button class="finance__edit finance__btn"><img :src="edit" alt="edit" class=""></button>
			<button class="finance__del finance__btn"><img :src="del" alt="del" class=""></button>
			<button class="finance__reset finance__btn"><img :src="reset" alt="del" class="finance__btn-img" @click="resetData"></button>
		</div>

		<div class="finance__table">
			<div class="finance__titles">
				<input type="checkbox" name="" id="" class="finance__checkbox">
				<div class="finance__field">
					<p class="finance__title">Дата</p>
					<img :src="sortingArrows" alt="switch" class="finance__switch" @click="sortDate">
				</div>

				<div class="finance__field">
					<p class="finance__title">Тип Операциии</p>
					<img :src="sortingArrows" alt="switch" class="finance__switch" @click="sortTypes">
				</div>

				<div class="finance__field">
					<p class="finance__title">Сумма</p>
					<img :src="sortingArrows" alt="switch" class="finance__switch" @click="sortPrice">
				</div>

				<div class="finance__field">
					<p class="finance__title">Плательщик</p>
					<img :src="sortingArrows" alt="switch" class="finance__switch">
				</div>

				<div class="finance__field">
					<p class="finance__title">Комментарий</p>
					<img :src="sortingArrows" alt="switch" class="finance__switch">
				</div>
			</div>

			<div class="finance__content">
				<FinanceItem v-for="(item, index) in items" :key="item.id" :item="item" :bg="index % 2 === 0 ? '#fff' : '#E2E2E2'"/>
				
			</div>
		</div>
	</div>
</template>

<script>
import add from '~/assets/finance/plus.svg'
import edit from '~/assets/finance/edit.svg'
import del from '~/assets/finance/del.svg'
import reset from '~/assets/finance/reset.png'

import sortingArrows from '~/assets/finance/SortingArrows.svg'

const defaultItems = [
				{
					id: 1,
					date: '01.01.2024',
					opType: 'Выплата ЗП',
					price: '4600',
					employe: 'Абдрахман У.',
					description: 'Отличная работа. Держи свою зарплату. Бери, иначе заставлю',
				},
				{
					id: 2,
					date: '01.02.2024',
					opType: 'Выплата ЗП',
					price: '3600',
					employe: 'Абдрахман У.',
					description: 'Отличная работа. Держи свою зарплату',
				},
				{
					id: 3,
					date: '01.03.2024',
					opType: 'Выплата ЗП',
					price: '5600',
					employe: 'Абдрахман У.',
					description: 'Отличная работа. Держи свою зарплату',
				},
				{
					id: 4,
					date: '04.03.2024',
					opType: 'Расход',
					price: '5000',
					employe: 'Абдрахман У.',
					description: 'Отличная работа. Держи свою зарплату',
				},
			];

const items = [
				{
					id: 1,
					date: '01.01.2024',
					opType: 'Выплата ЗП',
					price: '4600',
					employe: 'Абдрахман У.',
					description: 'Отличная работа. Держи свою зарплату. Бери, иначе заставлю',
				},
				{
					id: 2,
					date: '01.02.2024',
					opType: 'Выплата ЗП',
					price: '3600',
					employe: 'Абдрахман У.',
					description: 'Отличная работа. Держи свою зарплату',
				},
				{
					id: 3,
					date: '01.03.2024',
					opType: 'Выплата ЗП',
					price: '5600',
					employe: 'Абдрахман У.',
					description: 'Отличная работа. Держи свою зарплату',
				},
				{
					id: 4,
					date: '04.03.2024',
					opType: 'Расход',
					price: '5000',
					employe: 'Абдрахман У.',
					description: 'Отличная работа. Держи свою зарплату',
				},
			]

export default {
	data() {
		return {
			add: add,
			edit: edit,
			del: del,
			reset: reset,
			sortingArrows: sortingArrows,
			defaultItems: defaultItems,
			items: items,
			sortSwitchPrice: false,
			sortSwitchDate: false,
			sortSwitchType: 'all'
		}
	},
	setup() {
		
	},
	computed: {

	},
	methods: {
		resetData() {
			this.items = [...this.defaultItems];
		},
		sortPrice() {
			if(this.sortSwitchPrice) {
				this.sortPriceToSmall()

			} else {
				this.sortPriceToBig()

			}
			this.toogleSwitchPrice()
		},
		sortTypes() {
			this.toogleSwitchType();
			if (this.sortSwitchType === 'all') {
				this.items = [...this.defaultItems];
			} else {
				this.items = [...this.defaultItems.filter(this.filterType)]
			}
		},
		sortDate() {
			if (this.sortSwitchDate) {
				this.items = [...this.items.sort(this.sortDateToNew)]
			} else {
				this.items = [...this.items.sort(this.sortDateToOld)]
			}
			this.toogleSwitchDate()
		},
		filterType(item) {
			if (item.opType === this.sortSwitchType) {
				return item;
			}
		},
		toogleSwitchPrice() {
			this.sortSwitchPrice = !this.sortSwitchPrice;
		},
		toogleSwitchDate() {
			this.sortSwitchDate = !this.sortSwitchDate;
		},
		toogleSwitchType() {
			if (this.sortSwitchType === 'all') {
				this.sortSwitchType = 'Доход'
			}else if (this.sortSwitchType === 'Доход') {
				this.sortSwitchType = 'Расход'
			}else if (this.sortSwitchType === 'Расход') {
				this.sortSwitchType = 'Выплата ЗП'
			}else if (this.sortSwitchType === 'Выплата ЗП') {
				this.sortSwitchType = 'Возврат Средств'
			}else if (this.sortSwitchType === 'Возврат Средств') {
				this.sortSwitchType = 'all'
			}
		},
		sortDateToNew(a, b) {
			return new Date(b.date) - new Date(a.date);
		},
		sortDateToOld(a, b) {
			return new Date(a.date) - new Date(b.date);
		},
		sortPriceToSmall() {
			this.items.sort(function(data1, data2) {
				if(data1.price < data2.price) {
					return 1
				}
				if(data1.price > data2.price) {
					return -1
				}

				return 0
			})
		},
		sortPriceToBig() {
			this.items.sort(function(data1, data2) {
				if(data1.price > data2.price) {
					return 1
				}
				if(data1.price < data2.price) {
					return -1
				}

				return 0
			})
		}
	},
	props: {
		openPopup: Function
	}
}
</script>

<style lang="scss">
.finance {
	width: 90%;
	height: 70%;
	display: flex;
	flex-direction: row;
	gap: 25px;


	&__btns {
		display: flex;
		flex-direction: column;
		align-items: center;

		gap: 21px;

	}

	&__btn {
		border: none;
		background: none;
		outline: none;

		padding: 0;
		width: 50px;
		height: 50px;
		display: flex;
		align-items: center;
		justify-content: center;

		&-img {
			width: 30px;
			height: 30px;
		}

	}

	&__add {
	}

	&__edit {
	}

	&__del {
	}

	&__table {
		display: flex;
		flex-direction: column;

		border: #E2E2E2 solid 2px;
		border-radius: 10px;
		width: 95%;
	}

	&__titles {
		display: grid;
		grid-template-columns: 1fr 3fr 4fr 4fr 5fr 12fr;
		padding-left: 21px;
		padding-top: 23px;
		padding-bottom: 21px;
		padding-right: 21px;

		box-sizing: border-box;

		border-bottom: #E2E2E2 solid 2px;

	}

	&__checkbox {
		background: #B8B8B8;
		margin: 0;
		padding: 0;
		border: 0;
		border-radius: 5px;
		width: 23px;
		height: 23px;
	}

	&__field {
		display: flex;
		flex-direction: row;
		align-items: center;
		justify-content: center;
		gap: 5px;
	}

	&__title {

		margin: 0;

		font-family: Gilroy;
		font-size: 16px;
		font-weight: 400;
	}

	&__switch {
		width: 18px;
		height: 18px;

		cursor: pointer;
	}

	&__content {
		width: 100%;
		height: 100%;
	}
}

</style>