<script>
        import { getContext } from 'svelte'
        export let lapsi = lapsi
        export let index = index
        let displayDetails = false

        //FUNCTIONS
        function toggleDetails () {
            displayDetails = !displayDetails
        }
        const removeLapsi = getContext('removeLapsi',lapsi.id)
        const setEditedLapsi = getContext('setEditedLapsi',lapsi.id)
        const modifyLapsi = getContext('modifyLapsi', lapsi.id)


</script>

<style>

</style>

<!-- HTML -->

<article class='outer-container'>
    <div class='container'>
        <div class='row'><div>
                <h1>
                    {lapsi.name}    
                    <button class="amount-btn" on:click={toggleDetails}><i class="fa fa-caret-down" /></button>
                </h1>
                {#if displayDetails}
                <h3>
                    ID: {index+1}
                    ikä: {lapsi.age}
                </h3>
                {/if}

            </div>
            <div class='row-right'> 
                <button class="btn icon-size" on:click={() => setEditedLapsi(lapsi.id)}><i class="fa fa-edit edit-btn"></i></button>
                <button class="btn icon-size" on:click={() => removeLapsi(lapsi.id)}><i class="fa fa-trash delete-btn"></i></button>
            </div> 
        </div>
    </div>
</article>
