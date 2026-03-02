<script lang="ts">
	const faqs = [
		{
			question: 'What is the JLPT?',
			answer: 'The Japanese Language Proficiency Test (JLPT) is the most widely recognized test of Japanese language ability for non-native speakers. It has five levels: N5 (easiest) to N1 (most advanced). The test is held twice a year in July and December at locations worldwide.'
		},
		{
			question: 'What apps are available?',
			answer: 'We offer five specialized iOS apps: JLPT Practice Exams (100 full-length exams), JLPT Kanji Master (SRS-based kanji learning), JLPT Vocabulary (comprehensive vocab builder), JLPT Grammar (complete grammar reference), and JLPT Reading Practice (reading comprehension). Each app covers all JLPT levels from N5 to N1.'
		},
		{
			question: 'How much do the apps cost?',
			answer: 'Pricing is available on the App Store. Each app offers an annual subscription — check the individual app listings for current pricing and any available promotions.'
		},
		{
			question: 'Do the apps work offline?',
			answer: 'Yes! All apps are native iOS apps, so they work fully offline. Study on your commute, on a plane, or anywhere — no internet connection required.'
		},
		{
			question: 'How long does it take to pass each JLPT level?',
			answer: 'It varies by person, but typical timelines with consistent daily study (30–60 minutes) are: N5 in 2–3 months, N4 in 4–6 months, N3 in 8–12 months, N2 in 12–18 months, and N1 in 18–24+ months. Our SRS system is designed to make your study time as efficient as possible.'
		},
		{
			question: 'What makes JLPT Studio different from other apps?',
			answer: 'JLPT Studio apps are built specifically for the JLPT, unlike general Japanese learning apps. Every piece of content is mapped to the official test specifications. Our practice exams mirror the real test format, and our SRS is tuned for JLPT-specific vocabulary and kanji frequency. Each app is focused on one skill so you get depth, not surface-level coverage.'
		},
		{
			question: 'Do I need all five apps?',
			answer: 'Not necessarily! Each app is standalone — pick the ones that match your study needs. If you want full JLPT coverage, all five apps together form a comprehensive preparation system. Many students start with JLPT Practice Exams to identify weak areas, then add the other apps as needed.'
		}
	];

	let openIndex = $state<number | null>(null);

	function toggle(i: number) {
		openIndex = openIndex === i ? null : i;
	}
</script>

<section class="faq" id="faq">
	<div class="container">
		<h2 class="section-title reveal">Frequently Asked Questions</h2>
		<p class="section-subtitle reveal reveal-delay-1">
			Got questions? We've got answers. Can't find what you're looking for? Reach out to our support team.
		</p>

		<div class="faq-list">
			{#each faqs as faq, i}
				<div class="faq-item reveal reveal-delay-{Math.min(i + 1, 5)}" class:open={openIndex === i}>
					<button class="faq-question" onclick={() => toggle(i)}>
						<span>{faq.question}</span>
						<svg class="faq-chevron" width="20" height="20" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"><path d="m6 9 6 6 6-6"/></svg>
					</button>
					<div class="faq-answer">
						<p>{faq.answer}</p>
					</div>
				</div>
			{/each}
		</div>
	</div>
</section>

<style>
	.faq {
		padding: var(--section-padding);
		background: var(--lavender-50);
	}

	.faq-list {
		max-width: 720px;
		margin: 0 auto;
		display: flex;
		flex-direction: column;
		gap: 0.75rem;
	}

	.faq-item {
		background: white;
		border-radius: var(--radius-sm);
		border: 1px solid var(--gray-100);
		overflow: hidden;
		transition: all 0.3s ease;
	}

	.faq-item:hover {
		border-color: var(--lavender-200);
	}

	.faq-item.open {
		border-color: var(--lavender-300);
		box-shadow: var(--shadow-sm);
	}

	.faq-question {
		width: 100%;
		display: flex;
		align-items: center;
		justify-content: space-between;
		gap: 1rem;
		padding: 1.25rem 1.5rem;
		background: none;
		text-align: left;
		font-size: 1rem;
		font-weight: 600;
		color: var(--gray-800);
		font-family: var(--font-heading);
	}

	.faq-chevron {
		flex-shrink: 0;
		color: var(--gray-400);
		transition: transform 0.3s ease;
	}

	.faq-item.open .faq-chevron {
		transform: rotate(180deg);
		color: var(--lavender-500);
	}

	.faq-answer {
		max-height: 0;
		overflow: hidden;
		transition: max-height 0.3s ease;
	}

	.faq-item.open .faq-answer {
		max-height: 300px;
	}

	.faq-answer p {
		padding: 0 1.5rem 1.25rem;
		font-size: 0.95rem;
		color: var(--text-secondary);
		line-height: 1.7;
	}
</style>
