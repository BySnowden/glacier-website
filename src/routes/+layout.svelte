<script lang="ts">
    let { children } = $props();
</script>

<svelte:head>
    <link rel="icon" href="/images/icon-transparent.png" />
</svelte:head>

{@render children()}
