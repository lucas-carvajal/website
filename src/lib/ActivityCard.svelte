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
    <div class="info">
        <h4 class="title">{title}</h4>
        <p class="dates">{dates}</p>
    </div>
    <p class="description">{@html description}</p>
</div>

<style>
    .card {
        margin-top: 2em;
    }
    .header {
        display: flex;
        justify-content: space-between;
    }
    .institution {
        display: inline;
        margin: 0;
        padding: 0.1em;
        font-size: 1.5em;
        align-self: flex-end;
        font-weight: bolder;
    }
    .location {
        display: inline;
        float: right;
        margin: 0;
        padding: 0.1em;
        font-size: 1em;
        align-self: flex-end;
    }
    
    .info {
        display: flex;
        justify-content: space-between;
        margin-top: 0.5em;
    }
    .title {
        display: inline;
        margin: 0;
        padding: 0.1em;
        font-size: 1em;
    }
    .dates {
        display: inline;
        float: right;
        margin: 0;
        padding: 0.1em;
        font-size: 1em;
    }

    .description {
        margin-top: 0.5em;
        padding: 0.5em 1em;
        font-size: 1em;
    }
</style>
