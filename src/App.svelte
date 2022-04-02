<script>
	import ContactCard from "./ContactCard.svelte";
	let name = 'Sarunas';
	let userImage =""
	let title =""
	let description =""
	let age = 34;

	$: uppercaseName = name.toUpperCase ();
	$: console.log(name);
	$: if (name === 'SarunasDaunoras') {
		age = 40;
	}

	function incrementAge() {
		age +=1;
	}

	function changeName () {
		name = 'SarunasDaunoras'
	}

	// function nameInput(event) {
	// 	const enteredValue = event.target.value;
	// 	name = enteredValue;
	// }
	// only needed if using the value and oninput binding


</script>

<main>
	<h1> Hello {uppercaseName}, my age is {age}!</h1>
	<div class="inputs">
		<button on:mouseenter="{incrementAge}"> Change Age</button>
		<!-- <button on:click="{changeName}"> Change Name</button> -->
		<!-- <input type="text" value="{name}" on:input="{nameInput}"/> -->
		<!-- shorter version, good for forms etc -->
		<input type="text" bind:value="{name}" />
		<input type="text" bind:value="{title}" />
		<input type="text" bind:value="{userImage}" />
		<textarea rows="3" bind:value="{description}" textarea/>
	</div>
	<ContactCard 
		userName="{name}" 
		userJobTitle="{title}" 
		userDescription="{description}" 
		{userImage}
	/>


</main>

<style>
	main {
		text-align: center;
		padding: 1em;
		max-width: 240px;
		margin: 0 auto;
	}

	h1 {
		color: #ff3e00;
		text-transform: uppercase;
		font-size: 4em;
		font-weight: 100;
	}

	@media (min-width: 640px) {
		main {
			max-width: none;
		}
	}
	.inputs {
	display: flex;
	flex-direction: column;
	align-items: center;	
	}
</style>