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
	//SET EDITING VARIABLES
	let setName = ''
	let setAge = ''
	let setId = ''

	//RACTIVE
	$: isEditing = setId ? true : false 

	//FUNCTIONS
	function removeLapsi (id) {
		lapset = lapset.filter (item => item.id !== id)
		// console.log(lapset)
	}

	function addLapsi({name,age}) {
        let lapsi = {id: Math.random() * Date.now(), name, age}
		lapset = [lapsi, ...lapset ]
		// window.alert(lapsi)
        // console.log("lapset:", lapset)
	}

	function setEditedLapsi (id) {
		let lapsi = lapset.find(item => item.id === id)
		console.log("setEditedlapsi",lapsi)
		setId = lapsi.id
		setName = lapsi.name
		setAge = lapsi.age
		console.log("EDITING", lapsi.id, lapsi.name, lapsi.age)
	}
	function modifyLapsi({name, age}) {
		console.log("MODIFY", name, age)

	}
	//CONTEXT
	setContext('removeLapsi', removeLapsi)
	setContext('addLapsi', addLapsi)
	setContext('setEditedLapsi', setEditedLapsi)
	setContext('modifyLapsi', modifyLapsi)

</script>

<style>

</style>

<!-- HTML -->

<div class='bg-container'>
	<Navbar />
	<main >
		{console.log(isEditing)}
	<div class='page-content paragraph-text'>
		<Title title='Lista lapsista' />
		<LapsiForm name={setName} age={setAge} {isEditing}  />
		<LapsetList {lapset}/>
	</div>
	</main>
</div>
 