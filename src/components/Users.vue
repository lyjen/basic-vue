<template>
	<div class="users">
		<h1>Users</h1>
		<form v-on:submit="addUser">
			<input type="text" v-model="newUser.name" placeholder="Enter name"/>
			<br />
			<input type="text" v-model="newUser.email" placeholder="Enter email"/>
			<br />
			<input type="submit" value="Submit"/>
		</form>
		<ul> 
			<li v-for="user in users">
			<input type="checkbox" class="toggle" v-model="user.activated"/>
			<span :class="{activated: user.activated}">{{user.name}} : {{user.email}}
			<button v-on:click="deleteUser(user)">x</button>
			</span>
			</li>
		</ul>
	</div>
</template>

<script>
export default {
  name: 'Users',

  data(){
	return{
		newUser:{},
		users:[
		{
			name: 'LJ',
			email: 'mslyjen.lyj@email.com',
			activated: true
		},
		{
			name: 'Oliver',
			email: 'oliver@email.com',
			activated: true
		},
		{
			name: 'Chito',
			email: 'chito@email.com',
			activated: false
		}
		]
		}	
	},
	methods: {
		addUser: function(e){
			this.users.push({
			name: this.newUser.name,
			email: this.newUser.email,
			activated: false
			
			});
			e.preventDefault();
		},
		deleteUser: function(user){
			this.users.splice(this.users.indexOf(user),1);
		}
		
	},
	computed: {
		
	}
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
.users{
width:300px;
margin:0 auto;
padding: 0;

}
ul li{
list-style: none;
text-align: left;
}

.activated{
text-decoration: line-through;
}
</style>
