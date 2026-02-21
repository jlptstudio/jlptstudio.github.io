<script lang="ts">
	const features = [
		{
			icon: '🎯',
			title: 'All JLPT Levels',
			description: 'Comprehensive coverage from N5 beginner to N1 advanced. Every level, every skill, fully mapped to the official exam.',
			color: 'var(--lavender-100)',
			accent: 'var(--lavender-400)'
		},
		{
			icon: '漢',
			title: 'Kanji Mastery',
			description: 'Learn kanji through memorable mnemonics and animated stroke order. Build lasting visual associations for over 2,000 characters.',
			color: 'var(--peach-100)',
			accent: 'var(--peach-400)'
		},
		{
			icon: '📖',
			title: 'Vocabulary Builder',
			description: 'Master words in context with native example sentences, pitch accent guides, and real-world usage patterns.',
			color: 'var(--mint-100)',
			accent: 'var(--mint-400)'
		},
		{
			icon: '✏️',
			title: 'Grammar Guide',
			description: 'Crystal-clear grammar explanations with interactive practice exercises. From basic particles to advanced patterns.',
			color: 'var(--sky-100)',
			accent: 'var(--lavender-400)'
		},
		{
			icon: '📝',
			title: 'Simulated Exams',
			description: 'Realistic JLPT-style practice tests with detailed answer explanations. Know exactly where you stand before exam day.',
			color: 'var(--lavender-100)',
			accent: 'var(--lavender-500)'
		},
		{
			icon: '🧠',
			title: 'Spaced Repetition',
			description: 'Our SRS algorithm schedules reviews at the optimal moment. Scientifically proven to maximize long-term retention.',
			color: 'var(--peach-100)',
			accent: 'var(--coral-400)'
		}
	];
</script>

<section class="features" id="features">
	<div class="container">
		<h2 class="section-title reveal">Everything You Need to Pass</h2>
		<p class="section-subtitle reveal reveal-delay-1">
			A complete toolkit designed specifically for JLPT success. Every feature built with one goal: helping you pass.
		</p>

		<div class="features-grid">
			{#each features as feature, i}
				<div class="feature-card reveal reveal-delay-{Math.min(i + 1, 5)}">
					<div class="feature-icon" style="background: {feature.color}; color: {feature.accent};">
						{feature.icon}
					</div>
					<h3>{feature.title}</h3>
					<p>{feature.description}</p>
				</div>
			{/each}
		</div>
	</div>
</section>

<style>
	.features {
		padding: var(--section-padding);
		background: var(--bg-primary);
	}

	.features-grid {
		display: grid;
		grid-template-columns: repeat(3, 1fr);
		gap: 1.5rem;
	}

	.feature-card {
		padding: 2rem;
		background: white;
		border: 1px solid var(--gray-100);
		border-radius: var(--radius);
		transition: all 0.3s ease;
	}

	.feature-card:hover {
		transform: translateY(-4px);
		box-shadow: var(--shadow-lg);
		border-color: var(--lavender-200);
	}

	.feature-icon {
		width: 56px;
		height: 56px;
		display: flex;
		align-items: center;
		justify-content: center;
		border-radius: 14px;
		font-size: 1.5rem;
		margin-bottom: 1.25rem;
	}

	.feature-card h3 {
		font-size: 1.2rem;
		font-weight: 600;
		margin-bottom: 0.625rem;
	}

	.feature-card p {
		font-size: 0.95rem;
		color: var(--text-secondary);
		line-height: 1.6;
	}

	@media (max-width: 768px) {
		.features-grid {
			grid-template-columns: repeat(2, 1fr);
			gap: 1rem;
		}
	}

	@media (max-width: 480px) {
		.features-grid {
			grid-template-columns: 1fr;
		}
	}
</style>
