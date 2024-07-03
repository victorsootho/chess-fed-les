<script lang="ts">
	import { fly } from 'svelte/transition';

	import AnimatedHamburger from '$lib/AnimatedHamburger.svelte';
	import chessLogo from './chess-logo.svg';

	export let open = false;
	export let onClick = (): void => {
		open = !open;
	};
</script>

<header>
	<div class="main">
		<div class="logo">
			<a href="https://kit.svelte.dev">
				<img src={chessLogo} alt="A chess piece logo" />
			</a>
		</div>
		<AnimatedHamburger {open} {onClick} />
	</div>

	{#if open}
		<nav class="bg-red-500" transition:fly={{ y: -200, duration: 400 }}>
			<a href="/videos">Videos</a>
			<a href="/blog">Blog Post</a>
			<a href="/events">Events</a>
			<a href="/history">History</a>
			<a href="/milestones">Successes</a>
		</nav>
	{/if}
</header>

<style>
	header {
		position: relative;
		font-size: 2rem;
		color: var(--accent-color);
		background-color: var(--white);
		z-index: 2;
	}

	.main {
		display: flex;
		justify-content: space-between;
	}

	.logo {
		width: 3em;
		height: 3em;
	}

	.logo a {
		display: flex;
		align-items: center;
		justify-content: center;
		width: 100%;
		height: 100%;
	}

	.logo img {
		width: 2em;
		height: 2em;
		object-fit: contain;
	}

	nav {
		position: absolute;
		top: 100%; /* Ensure it is positioned below the header */
		left: 0;
		z-index: 10; /* Higher than the main content */
		width: 100%;
		padding: 1rem;
		display: flex;
		flex-direction: column;
		gap: 0.5rem;
		align-items: center;
		background-color: var(--white);
		box-shadow: 0 2px 10px rgba(0, 0, 0, 0.1); /* Add shadow for better visibility */
	}
</style>
