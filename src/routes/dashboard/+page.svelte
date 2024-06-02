<script lang="ts">
	import { goto } from '$app/navigation';
	import pb from '$lib/pocketbase';
	import { onMount } from 'svelte';

	onMount(() => {
		if (!pb.authStore.isValid) {
			// Redirect to the homepage if the authentication store is not valid
			goto('/');
		}
		console.log(pb.authStore.model);
	});

	function logout() {
		pb.authStore.clear();
		goto('/');
	}
</script>

<div class="container h-full mx-auto flex justify-center items-center">
	<div class="space-y-10 text-center flex flex-col items-center">
		<h2 class="h2">Welcome to the dashboard.</h2>
		<button class="btn variant-filled" on:click={logout}>Logout</button>
	</div>
</div>
