<template>
	<div>
		<div>
			<input type="text" v-on:input="getSurname" placeholder="Фамилия">
			<input type="text" v-on:input="getName" placeholder="Имя">
			<input type="text" v-on:input="getNumber" placeholder="Номер">
			<button v-on:click="add">Добавить</button>
			<button v-on:click="addToFavorite">Добавить в избранное</button>
		</div>
		<div>
			<button v-on:click="surnameSort">Сортировать по фамилии</button>
			<button v-on:click="nameSort">Сортировать по имени</button>
		</div>
		<ul>
			<li v-for="(card, item) in favContacts" :key="item">{{card.surname}} {{card.name}} {{card.number}}</li>
		</ul>
		<ul>
			<li v-for="(card, item) in contacts" :key="item">{{card.surname}} {{card.name}} {{card.number}}</li>
		</ul>
	</div>
</template>

<script>
	export default{
		data() {
			return{
			surname: '',
			name: '',
			number: '',
			contacts: [],
			favContacts: []
			};
		},
		methods: {
			getSurname: function (){
				this.surname = event.target.value;
			},
			getName: function (){
				this.name = event.target.value;
			},
			getNumber: function (){
				this.number = event.target.value;
			},
			add: function(){
				this.contacts.push({"surname" : this.surname, "name": this.name,"number": this.number});
			},
			addToFavorite: function(){
				this.favContacts.push({"surname" : this.surname, "name": this.name,"number": this.number});
			},
			surnameSort: function(){
				for (let i = 0; i < this.favContacts.length - 1; i ++){
					for (let j = 1; j < this.favContacts.length; j ++){
						if (this.favContacts[j].surname.localeCompare(this.favContacts[i].surname) < 0){
							[this.favContacts[i], this.favContacts[j]] = [this.favContacts[j], this.favContacts[i]];
						}
					}
				}
				this.favContacts.push();
				for (let i = 0; i < this.contacts.length - 1; i ++){
					for (let j = 1; j < this.contacts.length; j ++){
						if (this.contacts[j].surname.localeCompare(this.contacts[i].surname) < 0){
							[this.contacts[i], this.contacts[j]] = [this.contacts[j], this.contacts[i]];
						}
					}
				}
				this.contacts.push();
			},
			nameSort: function(){
				for (let i = 0; i < this.favContacts.length - 1; i ++){
					for (let j = 1; j < this.favContacts.length; j ++){
						if (this.favContacts[j].name.localeCompare(this.favContacts[i].name) < 0){
							console.log("asdasd");
							[this.favContacts[i], this.favContacts[j]] = [this.favContacts[j], this.favContacts[i]];
						}
					}
				}
				this.favContacts.push();
				for (let i = 0; i < this.contacts.length - 1; i ++){
					for (let j = 1; j < this.contacts.length; j ++){
						if (this.contacts[j].name.localeCompare(this.contacts[i].name) < 0){
							[this.contacts[i], this.contacts[j]] = [this.contacts[j], this.contacts[i]];
						}
					}
				}
				this.contacts.push();
			}
		}
	};

</script>