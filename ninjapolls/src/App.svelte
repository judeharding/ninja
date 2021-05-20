<!-- SCRIPTS -->
<script>
import Header from './components/Header.svelte';
import Footer from './components/Footer.svelte';
import CreatePollForm from './components/CreatePollForm.svelte';
import Tabs from './shared/Tabs.svelte';
import PollList from './components/PollList.svelte';

// tabs component
let items = ['Current Polls', 'Add New Poll'];
let activeItem =  'Current Polls';

const tabChange = (e) => {
	activeItem = e.detail;
}

 // polls
 let polls = [
    {
      id: 1,
      question: 'Python or JavaScript?',
      answerA: 'Python',
      answerB: 'JavaScript',
      votesA: 9,
      votesB: 15,
    },

		{
      id: 2,
      question: 'Peanut Butter or Nutella?',
      answerA: 'Peanut Butter',
      answerB: 'Nutella',
      votesA: 15,
      votesB: 9,
    },
  ];


const handleAdd = (e) => {
    const poll = e.detail;
    polls = [poll, ...polls];
    activeItem = 'Current Polls';
		// console.log('hello', polls);
  }

</script>

<!-- HTML COMPONENTS  -->
<Header/>
<main>
	<h1>Hello Ninjas!</h1>
	<p>"Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat. Duis aute irure dolor in reprehenderit in voluptate velit esse cillum dolore eu fugiat nulla pariatur. Excepteur sint occaecat cupidatat non proident, sunt in culpa qui officia deserunt mollit anim id est laborum."</p>

	<Tabs items={items} activeItem={activeItem} on:tabChange={tabChange}/>
	{#if activeItem === 'Current Polls' }
	<p> <em> Poll List component goes here </em> </p>
	<PollList polls={polls}/>
	{:else if activeItem === 'Add New Poll'}
	<!-- <p>New poll form component goes here</p> -->

	<CreatePollForm on:add={handleAdd} />
	{/if}

</main>
<Footer/>


<!-- STYLES  -->
<style>
	main {
	
		max-width: 960px;
		margin: 40px auto;
	}

	
</style>
