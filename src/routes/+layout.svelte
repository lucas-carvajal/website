<script lang="ts">
    import "@fontsource/montserrat"
</script>

<div class="nav">
    <div class="elements">
        <a href="/">Lucas</a>
        <a href="/work">Work</a>
        <a href="/education">Education</a>
        <a href="/projects">Projects</a>
        <a href="/contact">Contact</a>
    </div>
</div>
 
<div class="main">
    <slot></slot>
</div>

<style>
    .nav {
        position: fixed;
        width: 20%;
        height: 100%;
        top: 0;
        left: 0;
        z-index: 1;
        overflow-x: hidden;
        padding-top: auto;
        padding-bottom: auto;
        padding-left: 20px;
        display: flex;
        justify-content: center;
        align-items: center; 
    }

    a {
        display: block;
        margin: 0.8em 0;
        padding: 10px;
        text-decoration: none;
        color: black;
        font-size: 3vw;
    }

    a:hover {
        font-weight: 900;
    }

    .main {
        margin-left: 20%;
        padding: 4em;
    }

    div {
        font-family: 'montserrat', sans-serif;
    }
</style>
