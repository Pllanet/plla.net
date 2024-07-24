<script>
    import { onMount } from "svelte";
    import { goto } from '$app/navigation';

    let audio;
    let spotifyFrame;

    onMount(() => {
        audio.play();
    });

    // DOESNT WORK AND I DONT KNOW WHY. ITS NOT A BUG ITS A FEATURE
    let updateStatic = (event) => {
        let boundingBox = spotifyFrame.getBoundingClientRect();

        let distanceX = Math.abs(event.clientX - boundingBox.x);
        let distanceY = Math.abs(event.clientY - boundingBox.y);

        let magnitude = Math.sqrt(distanceX ^ 2 + distanceY ^ 2);
        
        audio.volume = magnitude / 35;
    }
</script>

<div class="flex flex-col h-screen" on:mousemove={updateStatic}>
    <div class="m-auto my-20" bind:this={spotifyFrame}>
        <iframe style="border-radius:12px pointer-events: none;" src="https://open.spotify.com/embed/album/26LYxs49CqC9WUZWiEK3jT?utm_source=generator" width="100%" height="352" frameBorder="0" allowfullscreen="" allow="autoplay; clipboard-write; encrypted-media; fullscreen; picture-in-picture" loading="lazy"></iframe>
    </div>

    <div class="m-auto my-0">
        <button class="bg-transparent text-white bold" on:click={() => {goto('/love')}}>
            i love you
        </button>
    </div>
</div>

<audio src="$lib/assets/noise.mp3" bind:this={audio} ></audio>

<style lang="postcss">
    :global(html) {
        background-color: #020305;
    }
</style>