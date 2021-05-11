<script>

	import Modal from './Modal.svelte';

let people = [

    { name: 'yoshi', beltColour: 'black', age: 25, id: 1 },
    { name: 'mario', beltColour: 'orange', age: 45, id: 2 },
    { name: 'luigi', beltColour: 'brown', age: 35, id: 3 }
  ];

	const handleDelete = (id) => {
		people = people.filter( (person) => person.id !=id);
	}

	let num = 3;

</script>

{#if num >20}
<p>GREATER THAN 20</p>
{:else if num > 5}
<p>GREATER THAN 5</p>
{:else}
<p>NOT GREATER THAN 5</p>
{/if}


<Modal />

<main>
	<!-- W/O LOOP 
	<div>
		<h4>{people[0].name}</h4>
		<p>{people[0].beltColour}</p> 
	</div>-->

		{#each people as person (person.id) } 
			<div>
				<h4>{person.name}</h4>
				<p>{person.age} years old,   {person.beltColour} belt </p>
				<!-- IN LINE FUNCTION BELOW TO HANDLE DELETE -->
				<button on:click={() => {
					handleDelete(person.id);
				}}>Delete</button>
			</div>
			{:else}<p>no data in arrayName</p> 
		{/each}


</main>

<style>
	main {
		text-align: center;
		padding: 1em;
		max-width: 240px;
		margin: 0 auto;
	}

	h4 {
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
</style>




<!-- TURN ON ENTIRE SCRIPT BLOCK -->
<!-- <script>
// taking data from the outside file - main.js aka world
	// export let name;


	// DEFINING DATA 
	let firstName = "yoshi";
	let lastName = "hendrix"
	let beltColor = "Black";

	// REACTIVE VALUE 
	$: fullName = `${firstName} ${lastName}`;
	const handleClick = () =>{
		beltColor = "orange";
	};

	// REACTIVE STATEMENT CODE BLOCK
	$: {
		console.log(beltColor);
		console.log(fullName);
	}


	const handleInput = (e) => {
		beltColor = e.target.value;
	};
</script> -->


<!-- TURN ON EACH LINE INDIVIDUALLY  -->
<!-- <main> -->

	<!-- <input type="text" bind:value={firstName}> -->
	<!-- <input type="text" bind:value={lastName}> -->

	<!-- OUTPUTTING DATA  -->
	<!-- <h1>Hello {fullName}!</h1> -->
	<!-- UPDATING CSS BASED ON USER ENTRY -->
	<!-- <p style="color: {beltColor}">{beltColor} Belt</p> -->

	<!-- HANDLE CLICK EVENTS -->
	<!-- <button on:click={handleClick}>Update Belt Color</button> -->

	<!-- <h3>1 way binding</h3> -->
	<!-- 1 WAY BINDING INPUT  -->
	<!-- <input type="text" on:input={handleInput}> -->

	<!-- <br> -->
	<!-- <h3>2 way binding</h3> -->

	<!-- 2 WAY BINDING INPUT  -->
	<!-- <input type="text" on:input={handleInput} value={beltColor}> -->
	<!-- shorthand 2way binding  -->
	<!-- <input type="text" bind:value={beltColor}> -->

	<!-- <br> -->

	<!-- <p>Visit the <a href="https://svelte.dev/tutorial">Svelte tutorial</a> to learn how to build Svelte apps.</p> -->
<!-- </main> -->

