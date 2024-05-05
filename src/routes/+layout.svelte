<script>
	import Header from "$lib/UI/Header.svelte";
	import LinkGrid from "$lib/LinkGrid.svelte";

	let title = "";
	let description = "";
	let url = "";
	let imageUrl = "";
	let userNotes= "";
	let tags = [];

	let links = [
		{
			id: 'l1',
			title: 'Marvel.com',
			url: 'https://www.marvel.com/',
			description: 'Marvel.com is the official site of Marvel Entertainment! Browse official Marvel movies, characters, comics, TV shows, videos, & more.',
			imageUrl: 'https://logos-world.net/wp-content/uploads/2020/11/Marvel-Logo-2000-2012.png',
			userNotes: 'Website for the best comic info',
			tags: ['comics', 'superheros', 'spiderman', 'wolverine']
		},
		{
			id: 'l2',
			title: 'dc.com',
			url: 'https://www.dc.com/comics',
			description: 'DC.com - Welcome to the Official Site for DC. DC is home to the world\'s Greatest Super Heroes, including SUPERMAN, BATMAN, WONDER WOMAN, GREEN LANTERN, THE FLASH, AQUAMAN and more',
			imageUrl: 'https://www.dc.com/img/dc-logo.svg',
			userNotes: 'Website for the 2nd best comic info',
			tags: ['comics', 'superheros', 'superman', 'batman']
		},
		{
			id: 'l3',
			title: 'NASA',
			url: 'https://www.nasa.gov/',
			description: 'NASA.gov brings you the latest news, images and videos from America\'s space agency, pioneering the future in space exploration, scientific discovery and aeronautics research.',
			imageUrl: 'https://www.nasa.gov/wp-content/themes/nasa/assets/images/nasa-logo.svg',
			userNotes: '',
			tags: ['space', 'astronomy', 'galaxies', 'solar system']
		},
		{
			id: 'l4',
			title: 'National Geographic',
			url: 'https://www.nationalgeographic.com/',
			description: 'Explore National Geographic. A world leader in geography, cartography and exploration.',
			imageUrl: 'https://logos-world.net/wp-content/uploads/2020/09/National-Geographic-Symbol.jpg',
			userNotes: 'Geography website with info from around',
			tags: ['lions', 'tigers', 'bears', 'oh my']
		},
		{
			id: 'l5',
			title: 'Image Comics',
			url: 'https://imagecomics.com/',
			description: 'Image is a comics and graphic novels publisher formed in 1992 by 7 of the comics industry\'s best-selling artists, and is the 3rd largest comics publisher in the United States.',
			imageUrl: 'https://www.cuartomundo.cl/wp-content/uploads/2015/09/Image-Comics-Logo-400x200.png',
			userNotes: 'Comic website for Spawn and other characters',
			tags: ['comics', 'superheros', 'spawn', 'transformers']
		},
		{
			id: 'l6',
			title: 'McFarlane',
			url: 'https://mcfarlane.com/',
			description: 'McFarlane.com :: The home all things Todd McFarlane',
			imageUrl: 'https://mcfarlane.com/wp-content/themes/mcfarlane/img/header-mcFarlane-logo.jpg',
			userNotes: 'Website of Todd McFarlange, creator of Spawn',
			tags: ['comics', 'superheros', 'spawn']
		}
	]

	function addLink() {
		const newLink = {
			id: Math.random.toString(),
			title: title,
			url: url,
			description: description,
			imageUrl: imageUrl,
			userNotes: userNotes,
			tags: tags
		};
		links = [newLink, ...links];

		title = '';
		url = '';
		description = '';
		imageUrl = '';
		userNotes = '';
		tags = '';
	}

	function deleteLink(deletedLink) {
		links = links.filter(link => link.id !== deletedLink.id);
	}

</script>


<main>
	<form on:submit|preventDefault={addLink}>
		<div class="form-control">
			<label for="title">Title</label>
			<input type="text" id="title" bind:value={title}>
		</div>
		<div class="form-control">
			<label for="url">Url</label>
			<input type="text" id="url" bind:value={url}>
		</div>
		<div class="form-control">
			<label for="description">Description</label>
			<input type="text" id="description" bind:value={description}>
		</div>
		<div class="form-control">
			<label for="imageUrl">ImageURL</label>
			<input type="text" id="imageUrl" bind:value={imageUrl}>
		</div>
		<div class="form-control">
			<label for="userNotes">User Notes</label>
			<input type="text" id="userNotes" bind:value={userNotes}>
		</div>
		<div class="form-control">
			<label for="tags">Tags</label>
			<input type="text" id="tags" bind:value={tags}>
		</div>
		<button type="submit">Save</button>
	</form>

	<Header />
	<LinkGrid on:delete={event => deleteLink(event.detail)} {links}/>
</main>

<style>
	main {
		margin-top: 5rem;
	}
</style>
