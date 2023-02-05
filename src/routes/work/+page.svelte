<script lang="ts">
    import ActivityCard from "../../lib/ActivityCard.svelte";
    import { workActivities } from "./content";
</script>

<h1>Work</h1>
<div class="wrapper">
    {#each workActivities as activity}
        <ActivityCard 
            institution={activity.institution}
            location={activity.location}
            title={activity.title}
            dates={activity.dates}
            description={activity.description}
        />
    {/each}
</div>

<style>
    .wrapper {
        margin: 0em 4em;
        padding: 0.5em;
    }
</style>
