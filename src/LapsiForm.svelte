<script>
    import { getContext } from 'svelte'
    export let name = ''
    export let age = null
    export let isEditing 
    // export let modifyLapsi
    // $: console.log('Name: ',{name},'Age: ', {age}) // Debug log
    $: isEmpty = !name || !age
    import LapsetData from './lapset'
  
    //VARIABLES
	let lapset = [...LapsetData]

    //FUNCTIONS
    function handleSubmit() {
        if (isEditing) {
            modifyLapsi({name, age})
        }
        else {
        addLapsi({name,age})
        // Cleaning addLapsi From inputs //
        name =''
        age=''}
    }
    const addLapsi = getContext('addLapsi',{name,age})
    const modifyLapsi = getContext('modifyLapsi',{name, age})
    const closeForm = getContext('closeForm')
</script>

<section class='form'>
<div class='outer-container'>
    <div class='container'>
        

        <div class='row'>   
        <h1>lisää lapsi</h1>
            <div class='row-right'> 
                <button type='button' class='close-btn' on:click={closeForm} ><i class='fa fa-times'>Sulje</button>
            </div>
        </div>
        <form on:submit|preventDefault={handleSubmit}>
        <div class='row'>
            <div class='form-control'> 
                <label for="name">Nimi</label>
                <input type='text' id='name' bind:value={name}>
            </div>
            
            <div class='form-control row-right'> 
                <label for="age">Ikä</label>
                <input type='text' id='age' bind:value={age}>
            </div>
        </div>
        {#if isEmpty}
        <div class='empty-warning'>
            <h1>Ole hyvä ja lisää nimi ja ikä</h1>
        </div>
        {/if}
        <button type='submit' class='btn btn-block' class:disabled={isEmpty} disabled={isEmpty}>
            {#if isEditing} Muuta tietoja {:else} Lisää lapsi {/if}
            </button>
    </form>        

    </div>
</div>
</section>