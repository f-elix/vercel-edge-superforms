<script lang="ts">
	import { superForm } from 'sveltekit-superforms';

	let { data } = $props();

	const superform = superForm(data.form);

	const { form, enhance, errors } = superform;
</script>

<form method="POST" use:enhance>
	<label for="name">
		<span>Name</span>
		<input type="text" name="name" bind:value={$form.name} />
		{#if $errors.name}
			<p class="error">{$errors.name}</p>
		{/if}
	</label>
	<label for="email">
		<span>Email</span>
		<input type="email" name="email" bind:value={$form.email} />
		{#if $errors.email}
			<p class="error">{$errors.email}</p>
		{/if}
	</label>
	<label for="message">
		<span>Message</span>
		<textarea name="message" bind:value={$form.message}></textarea>
		{#if $errors.message}
			<p class="error">{$errors.message}</p>
		{/if}
	</label>
	<button type="submit">Submit</button>
</form>

<style lang="postcss">
	form {
		display: flex;
		flex-direction: column;
		align-items: flex-start;
		gap: 1rem;
	}
	label {
		display: flex;
		flex-direction: column;
		align-items: flex-start;
		gap: 0.5rem;
	}
	.error {
		color: red;
	}
</style>
