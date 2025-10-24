<script>
	const themes = [
		{
			name: 'Ceramic',
			description: `Our “Playground” theme ceramics enhance any space with a bright color, crazy shapes and
				playful combinations.`,
			image: '/assets/playground.png',
			alt: 'Ceramic',
			color: 'primary'
		},
		{
			name: 'Zinc',
			description: `With plenty of different sizes, colors, textures and prints, we will for sure have something that catches your eye.`,
			image: '/assets/zinc.png',
			alt: 'Zinc',
			color: 'accent-blue'
		},
		{
			name: 'Wood',
			description: `With plenty of different sizes, colors, textures and prints, we will for sure have something that catches your eye.`,
			image: '/assets/wood.png',
			alt: 'Wood',
			color: 'accent-purple'
		},
		{
			name: 'Glass',
			description: `With plenty of different sizes, colors, textures and prints, we will for sure have something that catches your eye.`,
			image: '/assets/muguet.png',
			alt: 'Glass',
			color: 'accent-peach'
		}
	];
</script>

<section id="highlights" class="highlights">
	<h2>Highlights</h2>

	{#each themes as theme, index}
		<details
			class="highlight"
			style="--theme-color: var(--{theme.color}); --theme-color-dark: var(--{theme.color}-dark); --theme-color-light: var(--{theme.color}-light);"
			open={index === 0}
			name="themes"
		>
			<summary class="text">
				<h3>{theme.name}</h3>
				<p><span>{theme.name}</span></p>
			</summary>
			<div class="content">
				<p>{theme.description}</p>
				<img src={theme.image} alt={theme.alt} />
				<button>See More</button>
			</div>
		</details>
	{/each}
</section>

<style>
	.highlights {
		display: flex;
		flex-direction: column;
		gap: 0.5rem;
		overflow: hidden;
		max-width: 100vw;
	}

	details {
		display: flex;
		flex-direction: column;
		overflow: hidden;
	}

	h3 {
		font-size: 1.5rem;
		font-weight: 400;
	}

	/* only on larger screens */
	p:has(span) {
		display: flex;
	}

	@media (width < 35rem) {
		p:has(span) {
			display: none;
		}
	}

	.text {
		color: var(--neutral-100);
		background-color: var(--theme-color);
		display: flex;
		flex-direction: column;
		padding: 1rem;
	}

    /* animation needs some work, doesnt always work and often not on closing */
	.content {
		background-color: var(--theme-color-light);
		display: flex;
		flex-direction: column;
		gap: 1rem;

		transition:
			height 0.5s ease,
			content-visibility 0.5s ease allow-discrete;
		height: 0;
		overflow: clip;

		& button {
			background-color: var(--theme-color-dark);
			color: var(--neutral-100);
			width: fit-content;
			border: none;
			font-weight: 400;
			align-self: flex-end;
		}
	}

	/* Browser supports interpolate-size */
	@supports (interpolate-size: allow-keywords) {
		:root {
			interpolate-size: allow-keywords;
		}

		details[open] .content {
			height: auto;
            padding: 1rem;
		}
	}
</style>
