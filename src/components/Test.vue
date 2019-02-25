<template>
<div class="test2">
	<input type="text" v-model="title"/>
	<h1>{{title}}</h1>
	<p v-if="showName">- {{user.first_name}}</p>
	<p v-else> </p><br />
	<p v-for="item in items">{{item.title}}</p>
	<button v-on:click="greet('I miss you')">Try Me</button><br />
	<input type="text" v-on:keyup="pressKey" v-on:keyup.enter="hitEnter"/>
	<br />
	<label>First Name:</label> <input type="text" v-model="user.first_name" />
	<br />
	<label>Last Name:</label> <input type="text" v-model="user.last_name" />
	<h3>{{fullName}}</h3>
	<p>{{msg}}</p>
</div>
</template>

<script>
export default {
  name: 'Test',
  props: {
	msg: {
		type: String,
		default: 'Message'
	}
  },
  data(){
	return{
		title: ' ',
		user:{
			first_name: 'LJ',
			last_name: 'Lovendino'
		},
		showName: false,
		items:[
			{title: 'Plan1'},
			{title: 'Plan2'},
			{title: 'Plan3'},
		]
		}	
	},
	methods: {
		greet: function(greeting){
			alert(greeting);
		},
		pressKey: function(e){
		console.log(e.target.value);
		},
		hitEnter: function(){
		console.log('You hit enter');
		}
		
	},
	computed: {
		fullName: function(){
			return this.user.first_name+ ' '+this.user.last_name;
		}
	}
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>

</style>
