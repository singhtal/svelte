<script>
    export let artists;
</script>

    {#each artists as artist}
        <div
        class="list-group-item d-flex w-100 list-group-item-action
        align-items-center">
            <img
            class="rounded mr-3 d-block"
            src={artist.src}
            alt={`Photo of ${artist.name}`} />
        <div>
            <h4 class="mb-0">{artist.name}</h4>
            <p class="text-muted mb-0">{artist.reknown}</p>
        </div>
        </div>
       {:else}
       <p>No Data</p> 
    {/each}
