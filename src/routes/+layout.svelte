<script lang="ts">
	import '@fontsource/montserrat';
	import NavButton from '../lib/NavButton.svelte';

	var navOffset = '-200vw';
	var mainOffset = '0vw';

	let tick = 0;
	let interval: any;

	const animateMenuIn = () => {
		clearInterval(interval);
		tick = 0;
		interval = setInterval(() => {
			tick <= 200 ? setOffsets(`${-200 + tick}vw`, `${0 - tick}vw`) : setOffsets(`0vw`, `-200vw`);
			tick = tick + 2;
		}, 0.0001);
	};

	const animateMenuOut = () => {
		clearInterval(interval);
		tick = 0;
		interval = setInterval(() => {
			tick <= 200 ? setOffsets(`${0 - tick}vw`, `${-200 + tick}vw`) : setOffsets(`-200vw`, `0vw`);
			tick = tick + 2;
		}, 0.0001);
	};

	const setOffsets = (navLeftOffseet: string, mainRightOffset: string) => {
		navOffset = navLeftOffseet;
		mainOffset = mainRightOffset;
	};
</script>

<div class="nav" style="--nav-offset: {navOffset}">
	<button
		class="menu-button-nav"
		on:click={() => {
			animateMenuOut();
		}}
	>
		Close
	</button>
	<div class="elements">
		<NavButton route="/" title="Lucas" {animateMenuOut} />
		<NavButton route="/work" title="Work" {animateMenuOut} />
		<NavButton route="/education" title="Education" {animateMenuOut} />
		<NavButton route="/projects" title="Projects" {animateMenuOut} />
		<NavButton route="/contact" title="Contact" {animateMenuOut} />
	</div>
</div>

<div class="main" style="--main-offset: {mainOffset}">
	<button
		class="menu-button-main"
		on:click={() => {
			animateMenuIn();
		}}
	>
		Menu
	</button>
	<slot />
</div>

<style>
	.nav {
		position: fixed;
		width: 20vw;
		height: 100vh;
		top: 0;
		left: 0;
		z-index: 1;
		overflow-x: hidden;
		padding-top: auto;
		padding-bottom: auto;
		margin-left: 20px;
		display: flex;
		justify-content: center;
		align-items: center;
	}

	.main {
		margin-left: 20vw;
		padding: 4em;
	}

	.menu-button-main {
		visibility: hidden;
	}

	.menu-button-nav {
		visibility: hidden;
	}

	div {
		font-family: 'montserrat', sans-serif;
	}

	@media (max-width: 750px) {
		.nav {
			margin-left: 0;
			font-size: 2em;
			width: 100vw;
			left: var(--nav-offset);
			position: fixed;
			overflow: hidden;
		}

		.main {
			margin-left: 0;
			padding: 4em;
			font-size: 2vw;
			right: var(--main-offset);
			position: fixed;
			overflow: hidden;
		}

		.menu-button-nav {
			visibility: visible;
			position: fixed;
			top: 0;
			right: var(--nav-offset);
			font-size: 2vw;
			border: none;
			background: none;
			padding: 2em;
			color: navy;
		}

		.menu-button-main {
			visibility: visible;
			position: fixed;
			top: 0;
			right: var(--main-offset);
			font-size: 2vw;
			border: none;
			background: none;
			padding: 2em;
			color: navy;
		}
	}

	:global(body) {
		background-color: var(--background-color);
		color: var(--text-color);
	}

	:global(:root) {
		/* --background: #a1c8f4; */
		--background-color: #ffffff;
		/* --accent: #f4b087; */
		--accent-color: #000000;
		/* --text: #ffffff; */
		--text-color: #000000;
	}
</style>
