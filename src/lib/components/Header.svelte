<script>
	import { onMount } from 'svelte';

	let open = $state(false);
	let activeSection = $state('');

	function toggleMenu() {
		open = !open;
	}

	function closeMenu() {
		open = false;
	}

	onMount(() => {
		// close on click outside nav if its open
		// close on click link
		// close on esc
	});

	onMount(() => {
		// intersection observer to highlight active section in nav
		const sections = document.querySelectorAll('main section[id]'); // get all sections with id

		const observerOptions = {
			root: null,
			rootMargin: '0px',
			threshold: 0.6
		};

		const observer = new IntersectionObserver((entries) => {
			entries.forEach((entry) => {
				if (entry.isIntersecting) {
					activeSection = entry.target.id;
				}
			});
		}, observerOptions);

		sections.forEach((section) => {
			observer.observe(section);
		});
	});
</script>

<header>
	<nav class="nav">
		<a href="/" aria-label="home" class="logo" onclick={closeMenu}>
			<img src="/assets/logo.svg" alt="Logo" width="30" height="30" />
		</a>

		<button aria-label="Menu" aria-expanded={open} aria-controls="nav-links" onclick={toggleMenu}>
			<img src="/assets/hamburger.svg" alt="Menu Icon" width="30" height="30" />
		</button>

		<div class="nav-links" class:open aria-hidden={!open} id="nav-links">
			<ul class="links">
				<li><a href="#highlights" class:active={activeSection === 'highlights'}>Highlights</a></li>
				<li><a href="#about" class:active={activeSection === 'about'}>About</a></li>
				<li><a href="#products" class:active={activeSection === 'products'}>Products</a></li>
				<li class="cta">
					<a href="#contact" class:active={activeSection === 'contact'}>Contact</a>
				</li>
			</ul>
		</div>
	</nav>
</header>

<style>
	header {
		display: flex;
		width: 95%;
		max-width: 80rem;
		padding: 1rem;
		margin-top: 1rem;
		background-color: var(--neutral-50);
		box-shadow: var(--shadow);
		border-radius: 8px;
		position: fixed;
		top: 0.5rem;
	}

	nav {
		display: flex;
		align-items: center;
		justify-content: space-between;
		gap: 1rem;
		width: 100%;
		position: relative;
	}

	button {
		background: transparent;
		border: 0;
		padding: 0.25rem;
		display: none;
		cursor: pointer;
	}

    a.logo {
        display: flex;
        justify-content: center;
        align-items: center;
        height: 100%;
    }

	.nav-links {
		display: flex;
		transition: all 0.3s ease-in-out;
	}

	ul {
		display: flex;
		flex-direction: row;
		justify-content: center;
		align-items: center;
		gap: 1rem;
	}

	li.cta {
		background-color: var(--primary);
		border-radius: 50px;
		padding: 0.5rem 0.75rem;

		& a {
			color: var(--bg);
		}

		&:hover {
			background-color: var(--primary-dark);

			& a {
				color: var(--bg);
			}
		}
	}

	a {
		transition: 0.2s ease-in-out;
	}

	a.active {
		font-weight: bold;
		color: var(--primary);
	}

	@media (width < 40rem) {
		button {
			display: inline-flex;
		}

		.nav-links {
			position: absolute;
			top: 3.75rem;
			right: -1rem;
			background-color: var(--neutral-50);
			border-radius: 8px;
			box-shadow: var(--shadow);
			width: calc(100% - 3rem);
			min-width: 12rem;
			max-width: 320px;
			padding: 0.5rem 1rem;
			z-index: 50;

			/* Transition */
			opacity: 0;
			transform: translateY(-10px);
			pointer-events: none;
			transition:
				opacity 0.3s ease,
				transform 0.3s ease;
		}

		ul {
			flex-direction: column;
			align-items: start;
			gap: 0.5rem;
		}

		.nav-links.open {
			opacity: 1;
			transform: translateY(0);
			pointer-events: auto;
		}
	}
</style>
