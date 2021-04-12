<script context="module">
	import Client from './../../utils/client';
	import PrismicDom from 'prismic-dom';

	export async function load() {
		const document = await Client.getByUID(
			'pages',
			'lorem-ipsum-dolor-sit-amet-consectetur-adipiscing'
		);
		return {
			props: {
				document
			}
		};
	}
</script>

<script>
	export let document;
</script>

<main>
	<div class="container">
		<img src={document.data.image.url} alt={document.data.image.alt} />
		{@html PrismicDom.RichText.asHtml(document.data.title)}
		<div class="text">
			{@html PrismicDom.RichText.asHtml(document.data.content)}
		</div>
	</div>
</main>

<style>
	main {
		font-family: sans-serif;
	}

	.container {
		display: flex;
		flex-direction: column;
		align-items: center;
		padding: 0px 20px;
	}

	.container > * {
		width: 100%;
		max-width: 1024px;
	}

	.header {
		color: white;
		background-size: cover;
		min-height: 25vw;
		padding-top: 2rem;
		justify-content: flex-end;
	}
</style>
