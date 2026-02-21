<script lang="ts">
	const levels = [
		{
			level: 'N5',
			title: 'Beginner',
			description: 'Basic Japanese. Understand simple phrases, hiragana, katakana, and ~100 kanji.',
			items: ['Hiragana & Katakana', '~100 Kanji', '~800 Vocabulary', 'Basic Grammar'],
			color: 'var(--mint-300)',
			bg: 'var(--mint-50)'
		},
		{
			level: 'N4',
			title: 'Elementary',
			description: 'Everyday conversations. Read simple passages and understand basic dialogues.',
			items: ['~300 Kanji', '~1,500 Vocabulary', 'Conversational Grammar', 'Reading Passages'],
			color: 'var(--sky-200)',
			bg: 'var(--sky-50)'
		},
		{
			level: 'N3',
			title: 'Intermediate',
			description: 'Bridge level. Handle most everyday situations and read moderately complex texts.',
			items: ['~650 Kanji', '~3,750 Vocabulary', 'Complex Sentences', 'News Articles'],
			color: 'var(--lavender-300)',
			bg: 'var(--lavender-50)'
		},
		{
			level: 'N2',
			title: 'Upper-Intermediate',
			description: 'Professional level. Read newspapers, understand most natural-speed speech.',
			items: ['~1,000 Kanji', '~6,000 Vocabulary', 'Formal Expressions', 'Business Japanese'],
			color: 'var(--peach-300)',
			bg: 'var(--peach-50)'
		},
		{
			level: 'N1',
			title: 'Advanced',
			description: 'Near-native mastery. Comprehend complex texts, nuanced speech, and abstract topics.',
			items: ['~2,000 Kanji', '~10,000 Vocabulary', 'Academic Texts', 'Nuanced Expression'],
			color: 'var(--coral-400)',
			bg: 'var(--peach-50)'
		}
	];
</script>

<section class="levels" id="levels">
	<div class="container">
		<h2 class="section-title reveal">Every JLPT Level Covered</h2>
		<p class="section-subtitle reveal reveal-delay-1">
			Whether you're just starting or aiming for the top, we have a structured path for every level.
		</p>

		<div class="levels-grid">
			{#each levels as lvl, i}
				<div class="level-card reveal reveal-delay-{Math.min(i + 1, 5)}" style="--card-color: {lvl.color}; --card-bg: {lvl.bg};">
					<div class="level-badge">{lvl.level}</div>
					<h3>{lvl.title}</h3>
					<p class="level-desc">{lvl.description}</p>
					<ul>
						{#each lvl.items as item}
							<li>
								<svg width="16" height="16" viewBox="0 0 24 24" fill="none" stroke="var(--card-color)" stroke-width="2.5" stroke-linecap="round" stroke-linejoin="round"><path d="M20 6 9 17l-5-5"/></svg>
								{item}
							</li>
						{/each}
					</ul>
				</div>
			{/each}
		</div>
	</div>
</section>

<style>
	.levels {
		padding: var(--section-padding);
		background: var(--bg-primary);
	}

	.levels-grid {
		display: grid;
		grid-template-columns: repeat(5, 1fr);
		gap: 1.25rem;
	}

	.level-card {
		padding: 1.75rem 1.5rem;
		background: var(--card-bg);
		border: 1px solid color-mix(in srgb, var(--card-color) 25%, transparent);
		border-radius: var(--radius);
		text-align: center;
		transition: all 0.3s ease;
	}

	.level-card:hover {
		transform: translateY(-4px);
		box-shadow: var(--shadow-lg);
	}

	.level-badge {
		display: inline-flex;
		align-items: center;
		justify-content: center;
		width: 52px;
		height: 52px;
		background: var(--card-color);
		color: white;
		border-radius: 50%;
		font-family: var(--font-heading);
		font-size: 1.2rem;
		font-weight: 700;
		margin-bottom: 1rem;
	}

	.level-card h3 {
		font-size: 1.1rem;
		font-weight: 600;
		margin-bottom: 0.5rem;
	}

	.level-desc {
		font-size: 0.85rem;
		color: var(--text-secondary);
		line-height: 1.5;
		margin-bottom: 1rem;
	}

	.level-card ul {
		text-align: left;
	}

	.level-card li {
		display: flex;
		align-items: center;
		gap: 0.5rem;
		font-size: 0.825rem;
		color: var(--gray-600);
		padding: 0.3rem 0;
	}

	.level-card li svg {
		flex-shrink: 0;
	}

	@media (max-width: 1024px) {
		.levels-grid {
			grid-template-columns: repeat(3, 1fr);
		}
	}

	@media (max-width: 640px) {
		.levels-grid {
			grid-template-columns: repeat(2, 1fr);
			gap: 1rem;
		}
	}

	@media (max-width: 400px) {
		.levels-grid {
			grid-template-columns: 1fr;
		}
	}
</style>
