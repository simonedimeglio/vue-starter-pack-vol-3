<template>
	<div class="home">
		<h1>Lista di utenti</h1>
		<div v-for="user in users" :key="user.id">
			<h1>{{ user.name }}</h1>
		</div>
	</div>
</template>

<script>
export default {
	data() {
		return {
			users: [],
		};
	},
	// MOUNTED: Un hook del ciclo di vita del componente che viene eseguito dopo che il componente è stato montato.
	mounted() {
		// Esegui una richiesta fetch al server locale sulla porta 3000 per ottenere la lista degli utenti
		fetch("http://localhost:3000/users")
			.then((res) => res.json()) 										// Converti la risposta in formato JSON
			.then((data) => (this.users = data)) 					// Assegna i dati ottenuti dalla risposta alla variabile 'users'
			.catch((err) => console.error(err.message)); 	// Gestisci gli errori e stampali nella console
	},
};
</script>
