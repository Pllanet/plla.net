<script>
    import { goto } from '$app/navigation';
</script>

<div class="flex h-screen">
    <div class="m-auto my-20">
        <!--
            <h1 class="text-white bold text-2xl">
                Hi!
            </h1>
        -->
        <input on:click={() => {goto('/globe')}} class="size-16" type="image" src="$lib/assets/globe.png" alt="🌍" />
    </div>
</div>

<style lang="postcss">
    :global(html) {
        background-color: #020305;
    }
</style>