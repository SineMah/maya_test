<script>
	// import welcome from '$lib/images/svelte-welcome.webp';
	// import welcome_fallback from '$lib/images/svelte-welcome.png';

	import { onMount } from 'svelte';

	let appointmentsList = [];

	const load = async () => {
		const appointmentJson = await fetch('http://localhost:1337/api/appointments');
		const appointments = await appointmentJson.json();

		appointmentsList = [...appointmentsList, ...appointments.data];
	};

	onMount(async () => {
		await load();
	});
</script>

<svelte:head>
	<title>Termine</title>
	<meta name="description" content="Svelte demo app" />
</svelte:head>

<section>
	<div class="container mt-3 my-md-4 bd-layout">
		{#each appointmentsList as appointment}
            <div>{appointment.attributes.city}</div>
		{/each}
	</div>
</section>

<style>
	
</style>
