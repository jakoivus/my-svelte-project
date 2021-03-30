<script>;
	import {setContext, onMount, afterUpdate } from 'svelte'

	//COMPONENTS
	import Navbar from './Navbar.svelte'
	import LapsiForm from './LapsiForm.svelte'
	import Title from './Title.svelte'
	
	//DATA
	import LapsetList from './LapsetList.svelte'
	// import LapsetData from './lapset'
	
	//VARIABLES
	let lapset = []
	// let lapset = [...LapsetData]
	//SET EDITING VARIABLES
	let setName = ''
	let setAge = ''
	let setId = ''
	//TOGGLE FORM VARIABLES
	let isFormOpen = false

	//RACTIVE
	$: isEditing = setId ? true : false 

	//FUNCTIONS
	function showForm() {
		isFormOpen = true
	}
	
		function closeForm() {
		isFormOpen = false
		setId = ''
		setName = ''
		setAge = ''
	}

	function removeLapsi (id) {
		lapset = lapset.filter (item => item.id !== id)
		// console.log(lapset)
	}

	function addLapsi({name,age}) {
        let lapsi = {id: Math.random() * Date.now(), name, age}
		lapset = [lapsi, ...lapset ]
		closeForm()
		// window.alert(lapsi)
        // console.log("lapset:", lapset)
	}

	function setEditedLapsi (id) {
		let lapsi = lapset.find(item => item.id === id)
		// console.log("EDITING",lapsi)
		setId = lapsi.id
		setName = lapsi.name
		setAge = lapsi.age
		showForm()
	}
	function modifyLapsi({name, age}) {
		lapset = lapset.map(item => {
			return item.id === setId ? {...item, name, age} :item // {...item} Alternative
		})
		setId = ''
		setName = ''
		setAge = ''
		closeForm()
		// console.log("MODIFY", name, age)
	}
	//CONTEXT
	setContext('removeLapsi', removeLapsi)
	setContext('addLapsi', addLapsi)
	setContext('setEditedLapsi', setEditedLapsi)
	setContext('modifyLapsi', modifyLapsi)
	setContext('showForm', showForm)
	setContext('closeForm', closeForm)

	//LOCALSTORAGE
	function setLocalStorage() {
		localStorage.setItem("lapset", JSON.stringify(lapset))
	}

	//LIFECYCLE METHODS
	onMount (() => {lapset = localStorage.getItem('lapset') ? 
					JSON.parse(localStorage.getItem('lapset'))
					: []
	})

	afterUpdate(() =>{
		setLocalStorage()
	})


</script>

<style>

</style>

<!-- HTML -->

<div class='bg-container'>
	<Navbar />
	<main >
		<!-- {console.log(isEditing)} -->
	<div class='page-content paragraph-text'>
		<Title title='Lista lapsista' />
		{#if isFormOpen}
		<LapsiForm name={setName} age={setAge} {isEditing}  />
		{/if}
		<LapsetList {lapset}/>
	</div>
	</main>
</div>
 