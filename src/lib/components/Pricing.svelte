<script lang="ts">
	const plans = [
		{
			name: 'Monthly',
			price: '$30',
			period: '/month',
			description: 'Flexible month-to-month access',
			badge: '',
			features: [
				'All JLPT levels (N5–N1)',
				'Full kanji & vocabulary library',
				'Spaced repetition system',
				'Grammar lessons & exercises',
				'Simulated practice exams',
				'Progress tracking dashboard'
			],
			cta: 'Start Monthly',
			featured: false,
			note: 'Cancel anytime'
		},
		{
			name: 'Annual',
			price: '$200',
			period: '/year',
			description: 'Best value for serious learners',
			badge: 'RECOMMENDED',
			features: [
				'Everything in Monthly',
				'Save $160 per year',
				'Priority new features',
				'Offline study mode',
				'Advanced analytics',
				'Email support'
			],
			cta: 'Start Annual Plan',
			featured: true,
			note: 'Just $16.67/month'
		},
		{
			name: 'Lifetime',
			price: '$500',
			period: 'one-time',
			description: 'Pay once, learn forever',
			badge: 'LIMITED TIME',
			features: [
				'Everything in Annual',
				'All future content updates',
				'All future feature releases',
				'Community Discord access',
				'Priority support',
				'Founding member badge'
			],
			cta: 'Get Lifetime Access',
			featured: false,
			note: 'Never pay again'
		}
	];
</script>

<section class="pricing" id="pricing">
	<div class="container">
		<h2 class="section-title reveal">Simple, Transparent Pricing</h2>
		<p class="section-subtitle reveal reveal-delay-1">
			Start free, then pick the plan that matches your commitment. All plans include a 7-day free trial.
		</p>

		<div class="pricing-grid">
			{#each plans as plan, i}
				<div class="pricing-card reveal reveal-delay-{i + 1}" class:featured={plan.featured}>
					{#if plan.badge}
						<div class="pricing-badge" class:limited={plan.badge === 'LIMITED TIME'}>
							{plan.badge}
						</div>
					{/if}

					<h3>{plan.name}</h3>
					<p class="pricing-desc">{plan.description}</p>

					<div class="pricing-amount">
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

					<button class="btn {plan.featured ? 'btn-primary' : 'btn-secondary'} btn-full">
						{plan.cta}
					</button>
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

	@media (max-width: 768px) {
		.pricing-grid {
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
