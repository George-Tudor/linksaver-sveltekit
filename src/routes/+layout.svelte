<script>
	let username = '';
	let password = '';

	const registerUser = async () => {
		//API call to backend
	};
</script>

<form on:submit|preventDefault={registerUser}>
	<div class="form-control">
		<label for="username">Username:</label>
		<input id="username" type="text" bind:value={username} required>
	</div>
	<label for="password">Password:</label>
	<input id="password" type="password" bind:value={password} required>

	<button type="submit">Register</button>
</form>
