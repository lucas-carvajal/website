<script>
	import { onMount } from 'svelte';

	const greeting = "Hey, I'm Lucas";
	let typedChar = '';
	let index = 0;

	/**
	 * @type {string | number | NodeJS.Timer | undefined}
	 */
	let typewriter;

	const type = () => {
		typewriter = setInterval(typeChar, 80);
	};

	const typeChar = () => {
		if (index === 4) {
			typedChar += ' ';
			clearInterval(typewriter);
			setTimeout(() => type(), 320);
			index++;
		} else if (index < greeting.length) {
			typedChar += greeting[index];
			index++;
		} else {
			clearInterval(typewriter);
		}
	};

	onMount(() => {
		type();
	});
</script>

<div class="wrapper">
	<div class="content">
		<h1>{typedChar}</h1>
		<p>
			I'm currently finishing my Bachelor's Degree in Computer Science at the University of Bamberg
			and doing Backend Engineering as a Working Student at
			<a target="_blank" rel="noopener noreferrer" href="https://de.scalable.capital/en"
				>Scalable Capital</a
			>.
		</p>
	</div>
</div>

<style>
	.wrapper {
		display: flex;
		justify-content: center;
		align-items: center;
		height: 80vh;
	}

	.content {
		padding: 3em;
	}

	h1 {
		font-size: 4em;
		font-weight: 900;
	}

	div {
		font-family: 'montserrat', sans-serif;
		height: wrap-content;
		width: 100%;
	}

	a {
		text-decoration: none;
		color: var(--text-color);
	}
</style>
