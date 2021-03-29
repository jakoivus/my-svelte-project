<script>
    import { getContext } from 'svelte'
    let name =''
    let age = null
    $: console.log('Name: ',{name},'Age: ', {age})
    $: isEmpty = !name || !age
    import LapsetData from './lapset'
    // export let addLapsi

    //VARIABLES
	let lapset = [...LapsetData]

    //FUNCTIONS
    function handleSubmit({e}) {
        // e.preventDefault()
        addLapsi({name,age})
        window.alert("Submit pressed")
    }
    const addLapsi = getContext('addLapsi',{name,age})
    // const removeLapsi = getContext('remove',lapsi.id)
</script>

<section class='form'>
<div class='outer-container'>
    <div class='container'>
        

        <div class='row'>   
        <h1>lisää lapsi</h1>
            <div class='row-right'> 
                <button type='button' class='close-btn'><i class='fa fa-times'>Sulje</button>
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
        <button type='submit' class='btn btn-block' class:disabled={isEmpty} disabled={isEmpty}>Lisää lapsi</button>
    </form>        

    </div>
</div>
</section>