<script>;
	import {setContext } from 'svelte'
	import Navbar from './Navbar.svelte'
	import LapsiForm from './LapsiForm.svelte'
	import Title from './Title.svelte'
	
	//DATA
	import LapsetList from './LapsetList.svelte'
	import LapsetData from './lapset'
	
	//VARIABLES
	let lapset = [...LapsetData]

	//FUNCTIONS
	function removeLapsi (id) {
		lapset = lapset.filter (item => item.id !== id)
		console.log(lapset)
	}

	function addLapsi({name,age}) {
        let lapsi = {id: Math.random() * Date.now(), name, age}
		lapset = [lapsi, ...lapset ]
		window.alert(lapsi)
        console.log("lapset:", lapset)

	}
	//CONTEXT
	setContext('remove', removeLapsi)
	setContext('addLapsi', addLapsi)

</script>

<style>

</style>

<!-- HTML -->

<div class='bg-container'>
	<Navbar />
	<main >
	<div class='page-content paragraph-text'>
		<Title title='Lista lapsista' />
		<LapsiForm />
		<LapsetList {lapset}/>
	</div>
	</main>
</div>
 