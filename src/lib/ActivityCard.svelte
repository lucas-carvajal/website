<script lang="ts">
    export let institution: string;
    export let location: string;
    export let title: string;
    export let dates: string;
    export let description: string;
</script>

<div class="card">
    <div class="header">
        <h2 class="institution">{institution}</h2>
        <p class="location">{location}</p>
    </div>
    <h4 class="title">{title}</h4>
    <p class="dates">{dates}</p>
    <p class="description">{description}</p>
</div>

<style>
    .card {
        margin: 3em;
    }
    .header {
        display: inline;
    }
</style>