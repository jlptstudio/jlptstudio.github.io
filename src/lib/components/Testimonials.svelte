<script lang="ts">
	const testimonials = [
		{
			name: 'Sarah Chen',
			level: 'Passed N2',
			duration: 'Kanji Master & Vocab apps',
			text: 'The Kanji Master app completely changed how I study. The spaced repetition system meant I actually remembered what I learned instead of cramming and forgetting. Passed N2 on my first attempt!',
			avatar: 'SC'
		},
		{
			name: 'Marcus Webb',
			level: 'Passed N3',
			duration: 'Practice Exams app',
			text: 'The Practice Exams app was a game-changer. By the time I sat for N3, the real test felt familiar. 100 exams with detailed explanations for every answer helped me understand my weak points.',
			avatar: 'MW'
		},
		{
			name: 'Yuki Tanaka',
			level: 'Passed N1',
			duration: 'All 5 apps',
			text: 'As a heritage speaker, I could speak but struggled with reading and grammar. The Kanji Master and Grammar apps filled in the gaps perfectly. Finally passed N1!',
			avatar: 'YT'
		},
		{
			name: 'David Kim',
			level: 'Passed N4',
			duration: 'Vocabulary & Grammar apps',
			text: 'I tried three other apps before finding JLPT Studio. The difference is how the apps work together — vocabulary feeds into grammar, which shows up in the practice exams. It just clicks.',
			avatar: 'DK'
		},
		{
			name: 'Emily Rodriguez',
			level: 'Passed N2',
			duration: 'Vocabulary & Reading apps',
			text: 'The Vocabulary app with example sentences is incredible. Pairing it with the Reading Practice app made everything stick so much better than flashcard-only apps. Worth every penny.',
			avatar: 'ER'
		}
	];

	const colors = [
		'var(--lavender-300)',
		'var(--mint-300)',
		'var(--peach-300)',
		'var(--sky-200)',
		'var(--coral-400)'
	];
</script>

<section class="testimonials" id="testimonials">
	<div class="container">
		<h2 class="section-title reveal">Loved by Learners</h2>
		<p class="section-subtitle reveal reveal-delay-1">
			Join thousands of students who've passed the JLPT with our apps.
		</p>

		<div class="testimonials-grid">
			{#each testimonials as testimonial, i}
				<div class="testimonial-card reveal reveal-delay-{Math.min(i + 1, 5)}">
					<div class="stars">
						{#each Array(5) as _}
							<svg width="16" height="16" viewBox="0 0 24 24" fill="var(--peach-300)" stroke="none"><path d="M12 2l3.09 6.26L22 9.27l-5 4.87 1.18 6.88L12 17.77l-6.18 3.25L7 14.14 2 9.27l6.91-1.01L12 2z"/></svg>
						{/each}
					</div>
					<p class="testimonial-text">"{testimonial.text}"</p>
					<div class="testimonial-author">
						<div class="avatar" style="background: {colors[i]};">{testimonial.avatar}</div>
						<div>
							<div class="author-name">{testimonial.name}</div>
							<div class="author-meta">{testimonial.level} &middot; {testimonial.duration}</div>
						</div>
					</div>
				</div>
			{/each}
		</div>
	</div>
</section>

<style>
	.testimonials {
		padding: var(--section-padding);
		background: var(--lavender-50);
	}

	.testimonials-grid {
		display: grid;
		grid-template-columns: repeat(3, 1fr);
		gap: 1.5rem;
	}

	.testimonials-grid > :nth-child(4) {
		grid-column: 1 / 2;
	}

	.testimonials-grid > :nth-child(5) {
		grid-column: 2 / 4;
	}

	.testimonial-card {
		padding: 1.75rem;
		background: white;
		border-radius: var(--radius);
		box-shadow: var(--shadow-sm);
		border: 1px solid var(--gray-100);
		transition: all 0.3s ease;
	}

	.testimonial-card:hover {
		box-shadow: var(--shadow-md);
	}

	.stars {
		display: flex;
		gap: 2px;
		margin-bottom: 1rem;
	}

	.testimonial-text {
		font-size: 0.95rem;
		color: var(--gray-700);
		line-height: 1.7;
		margin-bottom: 1.25rem;
		font-style: italic;
	}

	.testimonial-author {
		display: flex;
		align-items: center;
		gap: 0.75rem;
	}

	.avatar {
		width: 40px;
		height: 40px;
		border-radius: 50%;
		display: flex;
		align-items: center;
		justify-content: center;
		color: white;
		font-weight: 600;
		font-size: 0.825rem;
		flex-shrink: 0;
	}

	.author-name {
		font-weight: 600;
		font-size: 0.925rem;
		color: var(--gray-800);
	}

	.author-meta {
		font-size: 0.8rem;
		color: var(--gray-400);
		margin-top: 0.1rem;
	}

	@media (max-width: 768px) {
		.testimonials-grid {
			grid-template-columns: 1fr;
		}

		.testimonials-grid > :nth-child(4),
		.testimonials-grid > :nth-child(5) {
			grid-column: auto;
		}
	}
</style>
