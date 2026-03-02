<script lang="ts">
	const features = [
		{
			icon: '📝',
			title: 'JLPT Practice Exams',
			description: '100 realistic full-length exams, auto-graded with detailed answer explanations. Only $1 per exam — invaluable preparation for all levels.',
			color: 'var(--lavender-100)',
			accent: 'var(--lavender-400)'
		},
		{
			icon: '漢',
			title: 'JLPT Kanji Master',
			description: 'SRS-based kanji learning designed specifically for each JLPT level. Covers all necessary kanji with practice quizzes to reinforce retention.',
			color: 'var(--peach-100)',
			accent: 'var(--peach-400)'
		},
		{
			icon: '📖',
			title: 'JLPT Vocabulary',
			description: 'Comprehensive vocabulary builder organized by JLPT level. SRS-powered reviews and practice quizzes to master every word you need.',
			color: 'var(--mint-100)',
			accent: 'var(--mint-400)'
		},
		{
			icon: '✏️',
			title: 'JLPT Grammar',
			description: 'Complete grammar reference and practice organized by JLPT level. From basic particles to advanced patterns, with exercises for every point.',
			color: 'var(--sky-100)',
			accent: 'var(--lavender-400)'
		},
		{
			icon: '📚',
			title: 'JLPT Reading Practice',
			description: 'Reading comprehension practice with passages at each JLPT level. Build the speed and accuracy you need for test day.',
			color: 'var(--lavender-100)',
			accent: 'var(--lavender-500)'
		},
		{
			icon: '📱',
			title: 'Designed for iOS',
			description: 'Native iOS apps built for a seamless study experience. Beautiful design, fast performance, and study anywhere — no internet required.',
			color: 'var(--peach-100)',
			accent: 'var(--coral-400)'
		}
	];
</script>

<section class="features" id="features">
	<div class="container">
		<h2 class="section-title reveal" id="apps">Everything You Need to Pass</h2>
		<p class="section-subtitle reveal reveal-delay-1">
			Five specialized iOS apps that work together as a complete JLPT preparation system. Each app focused on one skill, all designed by JLPT experts.
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
