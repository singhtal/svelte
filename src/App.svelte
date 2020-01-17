<script>
	import {onMount} from 'svelte';
	import ArtistList from './ArtistList.svelte';
	import ArtistSearch from './ArtistSearch.svelte';
	let searchTerm = "Jonathan G. Ferrar II";
	let artists = [];
	let displayList  = [];

	function filterList(list, query){
		return list.filter((item) => {
			return (
			item.name.toLowerCase().match(query.toLowerCase())
			)
		})
	}

	onMount(
		async () => {
			const res = await fetch(`data.json`);
			artists = await res.json();
			displayList = await artists;
		}
	);


</script>

<style lang="scss" global>
	@import "../node_modules/bootstrap/scss/bootstrap.scss";
	h1 {
		color: $primary;
	}
</style>
	<div class="container">
		<ArtistSearch bind:searchTerm

		on:updateSearch={
			()=>{
				displayList = filterList(artists, searchTerm);
			}
		}
		></ArtistSearch>
		<ArtistList bind:artists={displayList}></ArtistList>
	</div>
