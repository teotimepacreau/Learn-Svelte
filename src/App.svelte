<script>
	import FeedbackForm from "./components/FeedbackForm.svelte";

	import FeedbackList from "./components/FeedbackList.svelte";

	import FeedbackStats from "./components/FeedbackStats.svelte"

	let feedback = [
		{
			id: 1,
			rating: 10,
			text: 'Lorem ipsum dolor sit amet. '
		},

		{
			id: 2,
			rating: 8,
			text: 'Lorem ipsum dolor sit amet, consectetur adipiscing elit. Proin sit amet leo massa. '
		},
		{
			id: 3,
			rating: 6,
			text: 'Lorem ipsum dolor sit amet, consectetur adipiscing elit. Proin sit amet leo massa. Praesent suscipit suscipit lorem bibendum finibus. Mauris lacinia lobortis sapien at scelerisque. Vestibulum posuere odio quis diam bibendum, rhoncus molestie dolor commodo. Aliquam a velit sit amet lorem pellentesque varius non quis elit. Vivamus eget felis id tellus imperdiet efficitur in a nibh. Ut quis purus ullamcorper, interdum libero eget, vulputate mi. Vestibulum sollicitudin mollis odio, faucibus elementum purus condimentum sed. Phasellus ullamcorper augue nec purus interdum accumsan. Fusce malesuada magna vitae sodales posuere. Donec et porttitor nibh. Integer quis mauris felis. Donec ac odio ligula. '
		}
	]

	//NB D'AVIS
	$: count = feedback.length

	// MOYENNE DE TOUS LES AVIS
	$: average = feedback.reduce((previousValue, {rating})=> previousValue + rating, 0) / feedback.length

	// SUPPRESSION DE L'AVIS
	const deleteFeedback = (e)=>{
		const itemId = e.detail //detail est une propriété native de event

		feedback = feedback.filter((item)=>item.id != itemId) //on est obligé d'assigner pour que ça update
	}

</script>

<main>
	<div class="container">
		<FeedbackForm />
		<FeedbackStats {count} {average} />
		<FeedbackList {feedback} on:delete-feedback={deleteFeedback}/>
	</div>
</main>

<style>
	main {
		padding: var(--rythme);
	}
	.container {
		margin-inline: auto;
		max-width: 60ch;
	}
</style>