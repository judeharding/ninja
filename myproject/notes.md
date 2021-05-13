readme
New read me note

npx degit sveltejs/template myproject

npm install // to install all of the degit/svelte files

npm run dev

components end in .svelte

App.svelte has
3 sections within a .svelte file

- script tags - for the logic
- html template tags - for the dom
- style tags - for the css

main.js runs first and kickstarts the program

- import the app.svelte component

the index.html file serves up to the end user
the main.js file is injected into the index.html file
and the App.svelte file holds all the components executed in the main.js

REACTIVE VALUE IN THE SCRIPT
$: fullName = `${firstName} ${lastName}`;
const handleClick = () =>{
beltColor = "orange";
};

DEFINNING DATA IN THE SCRIPT
const handleInput = (e) => {
beltColor = e.target.value;
};

W/MATCHING CLICK HANDLER IN THE MAIN
<button on:click={handleClick}>Update Belt Color</button>

FOR EACH LOOP IN THE MAIN
{#each arrayName as arrayNameSingular (arrayNameSingular.id) }
...yourcode
<button on:click={() => {
handleDelete(person.id);
}}>Delete</button>
{:else}<p>no data in arrayName</p>
{/each}
W/MATCHING CLICK HANDLER IN TEH SCRIPT
const handleDelete = (id) => {
people = people.filter( (person) => person.id !=id);
};

CONDITIONALS / IF-CHECKS
Let num = 3 in the script

{#if num >20}

<p>GREATER THAN 20</p>
{:else if num > 5}
<p>GREATER THAN 5</p>
{:else}
<p>NOT GREATER THAN 5</p>
{/if}

SETTING PROPS
2 components - App and Modal
you can set properties in App and pass them into Modal

<!-- pasing props of message from App  -->
<Modal message="hey, i am a prop value" isPromo={true} />
<!-- accepting props into Modal (EXPORT is required)-->
<script>
  export let isPromo = false; // exporting b/c value may be passed in or set outside
  export let message = "default value"; //  if msg is being passed in if not, default value
</script>

COMMON EVENT MODIFIERS
once - makes sure the event can only fire once - removes handler
preventDefault - prevents the default action (like on a form)
self - only fires the event if the clicked element is the TARGET
ex: <button on:click|once={somefunc}></button>

SLOTS - a way to pass child-content into a component and render inside the component

to bind data:
let name;
<input type="text" bind:value={name}>
