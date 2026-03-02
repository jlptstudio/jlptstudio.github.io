<section class="how-it-works" id="how-it-works">
	<div class="container">
		<h2 class="section-title reveal">How It Works</h2>
		<p class="section-subtitle reveal reveal-delay-1">
			A simple path to JLPT success. No confusion, no guesswork.
		</p>

		<div class="steps">
			<div class="step reveal reveal-delay-1">
				<div class="step-number">1</div>
				<div class="step-icon">🎯</div>
				<h3>Choose Your Level</h3>
				<p>Pick your target JLPT level — N5 through N1. Every app is organized by level so you study exactly what you need.</p>
			</div>

			<div class="step-connector reveal reveal-delay-2">
				<svg width="60" height="24" viewBox="0 0 60 24" fill="none">
					<path d="M0 12h50m-8-8l8 8-8 8" stroke="var(--lavender-300)" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"/>
				</svg>
			</div>

			<div class="step reveal reveal-delay-2">
				<div class="step-number">2</div>
				<div class="step-icon">📱</div>
				<h3>Download the Apps</h3>
				<p>Get the apps you need from the App Store. Each one focuses on a key skill: kanji, vocabulary, grammar, reading, or practice exams.</p>
			</div>

			<div class="step-connector reveal reveal-delay-3">
				<svg width="60" height="24" viewBox="0 0 60 24" fill="none">
					<path d="M0 12h50m-8-8l8 8-8 8" stroke="var(--lavender-300)" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"/>
				</svg>
			</div>

			<div class="step reveal reveal-delay-3">
				<div class="step-number">3</div>
				<div class="step-icon">🏆</div>
				<h3>Pass the JLPT</h3>
				<p>Study with proven methods — SRS, practice quizzes, and full-length exams. Walk into your test with confidence.</p>
			</div>
		</div>
	</div>
</section>

<style>
	.how-it-works {
		padding: var(--section-padding);
		background: var(--lavender-50);
	}

	.steps {
		display: flex;
		align-items: flex-start;
		justify-content: center;
		gap: 1rem;
		max-width: 900px;
		margin: 0 auto;
	}

	.step {
		flex: 1;
		text-align: center;
		padding: 2rem 1.5rem;
		background: white;
		border-radius: var(--radius);
		box-shadow: var(--shadow-sm);
		position: relative;
	}

	.step-number {
		position: absolute;
		top: -12px;
		left: 50%;
		transform: translateX(-50%);
		width: 28px;
		height: 28px;
		background: linear-gradient(135deg, var(--lavender-400), var(--lavender-500));
		color: white;
		border-radius: 50%;
		font-family: var(--font-heading);
		font-weight: 700;
		font-size: 0.825rem;
		display: flex;
		align-items: center;
		justify-content: center;
	}

	.step-icon {
		font-size: 2.5rem;
		margin-bottom: 1rem;
	}

	.step h3 {
		font-size: 1.25rem;
		font-weight: 600;
		margin-bottom: 0.5rem;
	}

	.step p {
		font-size: 0.925rem;
		color: var(--text-secondary);
		line-height: 1.6;
	}

	.step-connector {
		display: flex;
		align-items: center;
		padding-top: 4rem;
	}

	@media (max-width: 768px) {
		.steps {
			flex-direction: column;
			gap: 1.5rem;
		}

		.step-connector {
			display: none;
		}
	}
</style>
