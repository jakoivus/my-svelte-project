<script>
    import Lapsi from './Lapsi.svelte'
    export let lapset = lapset
</script>
    <ul>
    {#each lapset as lapsi, index}
        <Lapsi {lapsi} {index} />
        {:else} <h1>Ei lapsia</h1>
    {/each}
    </ul>
    