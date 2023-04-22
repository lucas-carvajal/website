<script lang="ts">
	export let name: string;
	export let link: string;
	export let year: string;
	export let description: string;
	export let technologies: string;
</script>

<div class="card">
	<div class="header">
		<h2 class="project-name">
			<a target="_blank" rel="noopener noreferrer" href={link}>{name} &#8599;</a>
		</h2>
		<p class="year">{year}</p>
	</div>
	<p class="description">{@html description}</p>
	<p class="tech">Technologies I used and learned include: <br /> {@html technologies}</p>
</div>

<style>
	.card {
		margin-top: 2em;
	}
	.header {
		display: flex;
		justify-content: space-between;
	}

	.project-name {
		display: inline;
		margin: 0;
		padding: 0.1em;
		font-size: 1.5em;
		align-self: flex-end;
		font-weight: bolder;
	}

	.year {
		display: inline;
		float: right;
		margin: 0;
		padding: 0.1em;
		font-size: 1em;
		align-self: flex-end;
	}

	.description {
		padding: 0.5em 1em;
		font-size: 1em;
	}

	.tech {
		margin-top: 0.5em;
		padding: 0.5em 1em;
		font-size: 1em;
	}

	a {
		text-decoration: none;
		color: var(--text-color);
	}
</style>
