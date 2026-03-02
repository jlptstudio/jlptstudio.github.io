<script lang="ts">
	import { onMount } from 'svelte';

	let scrolled = $state(false);
	let mobileOpen = $state(false);

	const links = [
		{ href: '#apps', label: 'Apps' },
		{ href: '#how-it-works', label: 'How It Works' },
		{ href: '#levels', label: 'Levels' },
		{ href: '#testimonials', label: 'Testimonials' },
		{ href: '#pricing', label: 'Pricing' },
		{ href: '#faq', label: 'FAQ' }
	];

	onMount(() => {
		const handleScroll = () => {
			scrolled = window.scrollY > 20;
		};
		window.addEventListener('scroll', handleScroll, { passive: true });
		return () => window.removeEventListener('scroll', handleScroll);
	});

	function closeMobile() {
		mobileOpen = false;
	}
</script>

<nav class="nav" class:scrolled>
	<div class="nav-inner container">
		<a href="/" class="logo">
			<span class="logo-icon">学</span>
			<span class="logo-text">JLPT Studio</span>
		</a>

		<div class="nav-links" class:open={mobileOpen}>
			{#each links as link}
				<a href={link.href} onclick={closeMobile}>{link.label}</a>
			{/each}
			<a href="#" class="btn btn-primary btn-sm" onclick={closeMobile}>Download Apps</a>
		</div>

		<button
			class="hamburger"
			class:active={mobileOpen}
			onclick={() => (mobileOpen = !mobileOpen)}
			aria-label="Toggle menu"
		>
			<span></span>
			<span></span>
			<span></span>
		</button>
	</div>
</nav>

<style>
	.nav {
		position: fixed;
		top: 0;
		left: 0;
		right: 0;
		z-index: 100;
		padding: 1rem 0;
		transition: all 0.3s ease;
	}

	.nav.scrolled {
		background: rgba(255, 255, 255, 0.92);
		backdrop-filter: blur(12px);
		box-shadow: 0 1px 3px rgba(0, 0, 0, 0.06);
		padding: 0.6rem 0;
	}

	.nav-inner {
		display: flex;
		align-items: center;
		justify-content: space-between;
	}

	.logo {
		display: flex;
		align-items: center;
		gap: 0.5rem;
		font-family: var(--font-heading);
		font-weight: 700;
		font-size: 1.25rem;
		color: var(--gray-900);
	}

	.logo-icon {
		display: flex;
		align-items: center;
		justify-content: center;
		width: 36px;
		height: 36px;
		background: linear-gradient(135deg, var(--lavender-300), var(--lavender-500));
		color: white;
		border-radius: 10px;
		font-size: 1.25rem;
		font-family: serif;
	}

	.nav-links {
		display: flex;
		align-items: center;
		gap: 2rem;
	}

	.nav-links a {
		font-size: 0.925rem;
		font-weight: 500;
		color: var(--gray-600);
		transition: color 0.2s;
	}

	.nav-links a:hover {
		color: var(--lavender-500);
	}

	:global(.btn-sm) {
		padding: 0.6rem 1.4rem;
		font-size: 0.875rem;
	}

	.hamburger {
		display: none;
		flex-direction: column;
		gap: 5px;
		background: none;
		padding: 4px;
	}

	.hamburger span {
		display: block;
		width: 24px;
		height: 2px;
		background: var(--gray-700);
		border-radius: 2px;
		transition: all 0.3s ease;
	}

	.hamburger.active span:nth-child(1) {
		transform: rotate(45deg) translate(5px, 5px);
	}
	.hamburger.active span:nth-child(2) {
		opacity: 0;
	}
	.hamburger.active span:nth-child(3) {
		transform: rotate(-45deg) translate(5px, -5px);
	}

	@media (max-width: 768px) {
		.hamburger {
			display: flex;
		}

		.nav-links {
			position: fixed;
			top: 0;
			right: -100%;
			width: 280px;
			height: 100vh;
			flex-direction: column;
			background: white;
			padding: 5rem 2rem 2rem;
			gap: 1.5rem;
			box-shadow: var(--shadow-xl);
			transition: right 0.3s ease;
		}

		.nav-links.open {
			right: 0;
		}

		.nav-links a {
			font-size: 1.1rem;
		}
	}
</style>
