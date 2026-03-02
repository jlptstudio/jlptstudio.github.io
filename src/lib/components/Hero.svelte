<script lang="ts">
	const floatingKanji = ['漢', '字', '語', '文', '読', '書', '聞', '話', '学', '力', '日', '本'];
</script>

<section class="hero" id="hero">
	<div class="hero-bg">
		{#each floatingKanji as kanji, i}
			<span
				class="floating-kanji"
				style="
					left: {8 + (i % 4) * 25 + Math.sin(i) * 5}%;
					top: {10 + Math.floor(i / 4) * 30 + Math.cos(i) * 8}%;
					font-size: {2.5 + (i % 3) * 1.5}rem;
					opacity: {0.04 + (i % 3) * 0.02};
					animation-delay: {i * 0.8}s;
					animation-duration: {15 + (i % 5) * 5}s;
				"
			>
				{kanji}
			</span>
		{/each}
	</div>

	<div class="hero-content container">
		<div class="hero-badge reveal">
			<span class="badge-dot"></span>
			Now available on the App Store
		</div>

		<h1 class="hero-title reveal reveal-delay-1">
			Master the JLPT.<br />
			<span class="gradient-text">From N5 to N1.</span>
		</h1>

		<p class="hero-subtitle reveal reveal-delay-2">
			Five specialized iOS apps designed to help you conquer every section of the Japanese Language Proficiency Test.
			Kanji, vocabulary, grammar, reading, and full practice exams — all in your pocket.
		</p>

		<div class="hero-buttons reveal reveal-delay-3">
			<a href="#" class="btn btn-primary btn-lg">
				Download on App Store
				<svg width="20" height="20" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2.5" stroke-linecap="round" stroke-linejoin="round"><path d="M5 12h14"/><path d="m12 5 7 7-7 7"/></svg>
			</a>
			<a href="#apps" class="btn btn-secondary">View Apps</a>
		</div>

		<div class="hero-stats reveal reveal-delay-4">
			<div class="stat">
				<span class="stat-number">5</span>
				<span class="stat-label">Specialized Apps</span>
			</div>
			<div class="stat-divider"></div>
			<div class="stat">
				<span class="stat-number">100</span>
				<span class="stat-label">Practice Exams</span>
			</div>
			<div class="stat-divider"></div>
			<div class="stat">
				<span class="stat-number">N5–N1</span>
				<span class="stat-label">All JLPT Levels</span>
			</div>
		</div>
	</div>
</section>

<style>
	.hero {
		position: relative;
		min-height: 100vh;
		display: flex;
		align-items: center;
		padding: 7rem 0 4rem;
		background: linear-gradient(180deg, var(--lavender-50) 0%, var(--bg-primary) 100%);
		overflow: hidden;
	}

	.hero-bg {
		position: absolute;
		inset: 0;
		pointer-events: none;
	}

	.floating-kanji {
		position: absolute;
		font-family: 'Noto Serif JP', serif;
		color: var(--lavender-400);
		user-select: none;
		animation: float linear infinite;
	}

	@keyframes float {
		0%, 100% {
			transform: translateY(0px) rotate(0deg);
		}
		25% {
			transform: translateY(-20px) rotate(5deg);
		}
		50% {
			transform: translateY(-10px) rotate(-3deg);
		}
		75% {
			transform: translateY(-25px) rotate(3deg);
		}
	}

	.hero-content {
		position: relative;
		text-align: center;
		max-width: 800px;
		margin: 0 auto;
	}

	.hero-badge {
		display: inline-flex;
		align-items: center;
		gap: 0.5rem;
		padding: 0.5rem 1.25rem;
		background: white;
		border: 1px solid var(--lavender-200);
		border-radius: 50px;
		font-size: 0.875rem;
		font-weight: 500;
		color: var(--gray-600);
		margin-bottom: 2rem;
		box-shadow: var(--shadow-sm);
	}

	.badge-dot {
		width: 8px;
		height: 8px;
		background: var(--mint-400);
		border-radius: 50%;
		animation: pulse 2s ease-in-out infinite;
	}

	@keyframes pulse {
		0%, 100% { opacity: 1; }
		50% { opacity: 0.5; }
	}

	.hero-title {
		font-size: clamp(2.75rem, 6vw, 4.5rem);
		font-weight: 800;
		letter-spacing: -0.02em;
		margin-bottom: 1.5rem;
		line-height: 1.1;
	}

	.gradient-text {
		background: linear-gradient(135deg, var(--lavender-500), var(--coral-400));
		-webkit-background-clip: text;
		-webkit-text-fill-color: transparent;
		background-clip: text;
	}

	.hero-subtitle {
		font-size: clamp(1.075rem, 2vw, 1.25rem);
		color: var(--gray-500);
		line-height: 1.7;
		max-width: 620px;
		margin: 0 auto 2.5rem;
	}

	.hero-buttons {
		display: flex;
		align-items: center;
		justify-content: center;
		gap: 1rem;
		flex-wrap: wrap;
		margin-bottom: 3.5rem;
	}

	:global(.btn-lg) {
		padding: 1rem 2.5rem;
		font-size: 1.075rem;
	}

	.hero-stats {
		display: flex;
		align-items: center;
		justify-content: center;
		gap: 2rem;
	}

	.stat {
		display: flex;
		flex-direction: column;
		align-items: center;
	}

	.stat-number {
		font-family: var(--font-heading);
		font-size: 1.5rem;
		font-weight: 700;
		color: var(--gray-900);
	}

	.stat-label {
		font-size: 0.825rem;
		color: var(--gray-400);
		margin-top: 0.2rem;
	}

	.stat-divider {
		width: 1px;
		height: 40px;
		background: var(--gray-200);
	}

	@media (max-width: 768px) {
		.hero {
			padding: 6rem 0 3rem;
		}

		.hero-stats {
			gap: 1.25rem;
		}

		.stat-number {
			font-size: 1.25rem;
		}
	}

	@media (max-width: 480px) {
		.hero-buttons {
			flex-direction: column;
		}

		.hero-buttons .btn {
			width: 100%;
		}
	}
</style>
