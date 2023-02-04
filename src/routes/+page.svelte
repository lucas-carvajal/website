<script>
	import { onMount } from "svelte";

    const greeting = "Hey, I'm Lucas";
    let typedChar = "";
    let index = 0;

    /**
	 * @type {string | number | NodeJS.Timer | undefined}
	 */
    let typewriter;

    const type = () => {
        typewriter = setInterval(typeChar, 80);
    }

    const typeChar = () => {
        if (index === 4) {
            typedChar += " ";
            clearInterval(typewriter);
            setTimeout(() => type(), 320);
            index++;
        } else if (index < greeting.length) {
            typedChar += greeting[index];
            index++;
        } else {
            clearInterval(typewriter);
        }
    }

    onMount(() => {
        type();
    });
</script>

<div class="wrapper">
    <div class="content">
        <h1>{typedChar}</h1>
        <p>Lorem ipsum dolor sic est it</p>
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
</style>
