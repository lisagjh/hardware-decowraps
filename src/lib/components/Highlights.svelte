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
	<p>Take a look at some of our personal favorites - just a small peek into our vast collection.</p>

	<div class="wrapper">
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
	</div>
</section>

<style>
	.highlights {
		display: flex;
		flex-direction: column;
		gap: 1rem;
	}

	.wrapper {
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

	@media (width < 47rem) {
		p:has(span) {
			display: none;
		}
	}

	summary {
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

	@media (width > 47rem) {
		.wrapper {
			flex-direction: row;
			height: 500px; /* Of een andere gewenste hoogte */
		}

		details {
			display: flex;
			flex-direction: row;
			transition: flex 0.3s ease;
			flex: 0 0 auto;
		}

		details:not([open]) {
			flex: 0 0 auto;
			width: auto;
		}

		details[open] {
			flex: 1;
		}

		summary {
			display: flex;
			flex-direction: column;
			align-items: center;
			justify-content: end;
			padding: 1rem 0.5rem;
			cursor: pointer;
			position: relative;

			& h3 {
				position: absolute;
				top: 0;
				left: 50%;
				translate: -50% 1rem;
				font-size: 0.85rem;
				font-weight: 300;
			}

			& p {
				white-space: nowrap;
				font-size: 1.8rem;
				font-weight: 800;
				margin: 0;
				writing-mode: vertical-rl;
				transform: rotate(180deg);
			}
		}

		img {
			max-width: 30rem;
			object-fit: contain;
		}

		.content {
			background-color: var(--theme-color-light);
			display: flex;
			flex-direction: column;
			gap: 1rem;
			padding: 2rem;
			width: 100%;
			min-height: fit-content;
			height: 100%;
			transition: all 0.3s ease;
			overflow-y: auto;

            & img {
                height: 100%;
                width: 100%;
                max-width: 100%;
                object-fit: cover;

            }

			& button {
				background-color: var(--theme-color-dark);
				color: var(--neutral-100);
				padding: 0.75rem 1.5rem;
				width: fit-content;
				border: none;
				font-weight: 400;
				align-self: flex-end;
				cursor: pointer;
			}
		}

		details[open] .content {
			height: 100%;
		}
	}
</style>
