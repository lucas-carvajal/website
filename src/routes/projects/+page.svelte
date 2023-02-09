<script lang="ts">
    import ProjectCard from "../../lib/ProjectCard.svelte";
    import { projects } from "./content";
</script>

<h1>Projects</h1>

<div class="wrapper">
    <p>Small selection for now. Will add more in the future.</p>
    {#each projects as project}
        <ProjectCard 
            name={project.name} 
            link={project.link} 
            year={project.year}
            description={project.description} 
            technologies={project.technologies}
        />
    {/each}
</div>


<style>
    .wrapper {
        margin: 0em 4em;
        padding: 0.5em;
    }
</style>

