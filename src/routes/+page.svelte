<section id="hero" class="hero">
	<div class="hero-text">
		<h1>Explore our collection</h1>
		<p>
			Discover our showroom pieces, select your favorites and prepare your next project request.
		</p>
		<div class="buttons">
			<a href="#showroom">View our Showroom</a>
			<a href="#contact">Contact</a>
		</div>
	</div>

	<img
		src="/assets/showroom.png"
		alt="A display featuring small wooden vases with white flowers and trailing greenery, geometric wooden objects with small glass tubes on a natural fiber placemat, stacked books, and a decorative hanging terrarium with plants on a white surface, set against dark open shelving with ceramics"
		width="250"
	/>
</section>

<section id="highlights">
	<h2>Our Highlights</h2>
	<p>Wow so cool</p>
</section>

<style>
	section {
		margin-top: 2rem;
		display: flex;
		flex-direction: column;
		gap: 1.5rem;
		padding: 1rem;
		min-height: 75vh;
		width: 100%;
	}

	.hero .hero-text {
		display: flex;
		flex-direction: column;
		gap: 1rem;
	}

	.buttons {
		display: flex;
		flex-direction: row;
		gap: 1rem;

		a {
			display: flex;
			width: fit-content;
			text-align: center;
			padding: 0.5rem 1rem;
			border-radius: 8px;
		}

		a:first-of-type {
			background-color: var(--primary-light);
			color: var(--text);
		}

        a:last-of-type {
            background-color: var(--bg);
            color: var(--text);
            box-shadow: var(--shadow-accent);
        }
	}

	.hero img {
		width: 100%;
		border-radius: 6px;
	}
</style>
