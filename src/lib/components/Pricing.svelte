<script lang="ts">
	const plans = [
		{
			name: 'JLPT Practice Exams',
			price: '$50',
			period: '/year',
			description: '100 full-length exams — only $1 per exam',
			badge: 'HALF PRICE',
			features: [
				'100 realistic full-length exams',
				'Auto-graded with explanations',
				'All JLPT levels (N5–N1)',
				'Designed by JLPT experts',
				'Detailed score breakdowns',
				'Only $1 per exam'
			],
			cta: 'Download',
			featured: true,
			note: '$100/year — 50% off for a limited time',
			strikePrice: '$100'
		},
		{
			name: 'JLPT Kanji Master',
			price: '$50',
			period: '/year',
			description: 'SRS-based kanji learning by JLPT level',
			badge: 'HALF PRICE',
			features: [
				'All kanji for every JLPT level',
				'Spaced repetition system',
				'Practice quizzes',
				'Stroke order animations',
				'Mnemonic aids',
				'Progress tracking'
			],
			cta: 'Download',
			featured: false,
			note: '$100/year — 50% off for a limited time',
			strikePrice: '$100'
		},
		{
			name: 'JLPT Vocabulary',
			price: '$50',
			period: '/year',
			description: 'Comprehensive vocab by JLPT level',
			badge: 'HALF PRICE',
			features: [
				'Vocabulary for all JLPT levels',
				'Spaced repetition system',
				'Practice quizzes',
				'Example sentences',
				'Audio pronunciation',
				'Progress tracking'
			],
			cta: 'Download',
			featured: false,
			note: '$100/year — 50% off for a limited time',
			strikePrice: '$100'
		}
	];

	const morePlans = [
		{
			name: 'JLPT Grammar',
			price: '$50',
			period: '/year',
			description: 'Complete grammar reference & practice',
			badge: 'HALF PRICE',
			features: [
				'All grammar points by JLPT level',
				'Clear explanations & examples',
				'Interactive exercises',
				'Pattern recognition drills',
				'Progress tracking'
			],
			cta: 'Download',
			featured: false,
			note: '$100/year — 50% off for a limited time',
			strikePrice: '$100'
		},
		{
			name: 'JLPT Reading Practice',
			price: '$50',
			period: '/year',
			description: 'Reading comprehension by JLPT level',
			badge: 'HALF PRICE',
			features: [
				'Passages at every JLPT level',
				'Comprehension questions',
				'Timed reading practice',
				'Vocabulary highlights',
				'Progress tracking'
			],
			cta: 'Download',
			featured: false,
			note: '$100/year — 50% off for a limited time',
			strikePrice: '$100'
		}
	];
</script>

<section class="pricing" id="pricing">
	<div class="container">
		<div class="sale-banner reveal">LIMITED TIME: All apps half price — $50/year each instead of $100!</div>
		<h2 class="section-title reveal">Simple, Transparent Pricing</h2>
		<p class="section-subtitle reveal reveal-delay-1">
			Each app is available separately so you can choose exactly what you need. Limited supply of discounted subscriptions available.
		</p>

		<div class="pricing-grid">
			{#each plans as plan, i}
				<div class="pricing-card reveal reveal-delay-{i + 1}" class:featured={plan.featured}>
					{#if plan.badge}
						<div class="pricing-badge limited">
							{plan.badge}
						</div>
					{/if}

					<h3>{plan.name}</h3>
					<p class="pricing-desc">{plan.description}</p>

					<div class="pricing-amount">
						{#if plan.strikePrice}
							<span class="strike-price">{plan.strikePrice}</span>
						{/if}
						<span class="price">{plan.price}</span>
						<span class="period">{plan.period}</span>
					</div>

					<p class="pricing-note">{plan.note}</p>

					<ul class="pricing-features">
						{#each plan.features as feature}
							<li>
								<svg width="18" height="18" viewBox="0 0 24 24" fill="none" stroke={plan.featured ? 'var(--lavender-400)' : 'var(--mint-400)'} stroke-width="2.5" stroke-linecap="round" stroke-linejoin="round"><path d="M20 6 9 17l-5-5"/></svg>
								{feature}
							</li>
						{/each}
					</ul>

					<a href="#" class="btn {plan.featured ? 'btn-primary' : 'btn-secondary'} btn-full">
						{plan.cta}
					</a>
				</div>
			{/each}
		</div>

		<div class="pricing-grid pricing-grid-2">
			{#each morePlans as plan, i}
				<div class="pricing-card reveal reveal-delay-{i + 1}" class:featured={plan.featured}>
					{#if plan.badge}
						<div class="pricing-badge limited">
							{plan.badge}
						</div>
					{/if}

					<h3>{plan.name}</h3>
					<p class="pricing-desc">{plan.description}</p>

					<div class="pricing-amount">
						{#if plan.strikePrice}
							<span class="strike-price">{plan.strikePrice}</span>
						{/if}
						<span class="price">{plan.price}</span>
						<span class="period">{plan.period}</span>
					</div>

					<p class="pricing-note">{plan.note}</p>

					<ul class="pricing-features">
						{#each plan.features as feature}
							<li>
								<svg width="18" height="18" viewBox="0 0 24 24" fill="none" stroke="var(--mint-400)" stroke-width="2.5" stroke-linecap="round" stroke-linejoin="round"><path d="M20 6 9 17l-5-5"/></svg>
								{feature}
							</li>
						{/each}
					</ul>

					<a href="#" class="btn btn-secondary btn-full">
						{plan.cta}
					</a>
				</div>
			{/each}
		</div>
	</div>
</section>

<style>
	.pricing {
		padding: var(--section-padding);
		background: var(--bg-primary);
	}

	.pricing-grid {
		display: grid;
		grid-template-columns: repeat(3, 1fr);
		gap: 1.5rem;
		max-width: 1000px;
		margin: 0 auto;
		align-items: start;
	}

	.pricing-card {
		padding: 2.5rem 2rem;
		background: white;
		border: 1px solid var(--gray-200);
		border-radius: var(--radius);
		position: relative;
		transition: all 0.3s ease;
	}

	.pricing-card:hover {
		box-shadow: var(--shadow-lg);
	}

	.pricing-card.featured {
		border: 2px solid var(--lavender-400);
		box-shadow: var(--shadow-xl);
		transform: scale(1.05);
		background: linear-gradient(180deg, var(--lavender-50) 0%, white 30%);
	}

	.pricing-card.featured:hover {
		transform: scale(1.07);
	}

	.pricing-badge {
		position: absolute;
		top: -12px;
		left: 50%;
		transform: translateX(-50%);
		padding: 0.35rem 1rem;
		background: linear-gradient(135deg, var(--lavender-400), var(--lavender-500));
		color: white;
		font-size: 0.7rem;
		font-weight: 700;
		letter-spacing: 0.05em;
		border-radius: 50px;
		white-space: nowrap;
	}

	.pricing-badge.limited {
		background: linear-gradient(135deg, var(--peach-300), var(--coral-400));
	}

	.pricing-card h3 {
		font-size: 1.3rem;
		font-weight: 600;
		margin-bottom: 0.25rem;
	}

	.pricing-desc {
		font-size: 0.875rem;
		color: var(--text-secondary);
		margin-bottom: 1.5rem;
	}

	.pricing-amount {
		display: flex;
		align-items: baseline;
		gap: 0.25rem;
		margin-bottom: 0.25rem;
	}

	.price {
		font-family: var(--font-heading);
		font-size: 3rem;
		font-weight: 700;
		color: var(--gray-900);
	}

	.period {
		font-size: 1rem;
		color: var(--gray-400);
	}

	.pricing-note {
		font-size: 0.825rem;
		color: var(--lavender-400);
		font-weight: 500;
		margin-bottom: 1.5rem;
	}

	.pricing-features {
		margin-bottom: 2rem;
	}

	.pricing-features li {
		display: flex;
		align-items: center;
		gap: 0.625rem;
		font-size: 0.9rem;
		color: var(--gray-600);
		padding: 0.45rem 0;
	}

	.pricing-features li svg {
		flex-shrink: 0;
	}

	:global(.btn-full) {
		width: 100%;
	}

	.sale-banner {
		text-align: center;
		padding: 1rem 2rem;
		background: linear-gradient(135deg, var(--peach-300), var(--coral-400));
		color: white;
		font-weight: 700;
		font-size: 1.1rem;
		border-radius: var(--radius);
		margin-bottom: 2rem;
	}

	.strike-price {
		font-family: var(--font-heading);
		font-size: 1.5rem;
		font-weight: 500;
		color: var(--gray-400);
		text-decoration: line-through;
		margin-right: 0.25rem;
	}

	.pricing-grid-2 {
		grid-template-columns: repeat(2, 1fr);
		max-width: 660px;
		margin-top: 1.5rem;
	}

	@media (max-width: 768px) {
		.pricing-grid {
			grid-template-columns: 1fr;
			max-width: 400px;
		}

		.pricing-grid-2 {
			grid-template-columns: 1fr;
			max-width: 400px;
		}

		.pricing-card.featured {
			transform: none;
			order: -1;
		}

		.pricing-card.featured:hover {
			transform: none;
		}
	}
</style>
