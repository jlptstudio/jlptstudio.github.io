<script lang="ts">
	let submitted = $state(false);
	let submitting = $state(false);

	async function handleSubmit(e: SubmitEvent) {
		e.preventDefault();
		submitting = true;
		const form = e.target as HTMLFormElement;
		const data = new FormData(form);

		try {
			const res = await fetch('https://formsubmit.co/ajax/mail@jlpt.studio', {
				method: 'POST',
				headers: { 'Content-Type': 'application/json', 'Accept': 'application/json' },
				body: JSON.stringify(Object.fromEntries(data))
			});
			if (res.ok) {
				submitted = true;
				form.reset();
			}
		} catch {
			const name = data.get('name');
			const email = data.get('email');
			const message = data.get('message');
			window.location.href = `mailto:mail@jlpt.studio?subject=Contact from ${name}&body=${message}%0A%0AFrom: ${name} <${email}>`;
		} finally {
			submitting = false;
		}
	}
</script>

<section id="contact" class="contact">
	<div class="container">
		<div class="section-header reveal">
			<span class="section-badge">✉️ Get in Touch</span>
			<h2>Questions? We'd Love to Help</h2>
			<p class="section-desc">Whether you have questions about our apps, need study advice, or want to learn more about JLPT Studio — we're here for you.</p>
		</div>

		<div class="contact-grid reveal">
			{#if submitted}
				<div class="success-message">
					<div class="success-icon">✓</div>
					<h3>Message Sent!</h3>
					<p>Thank you for reaching out. We'll get back to you within 24 hours.</p>
					<button class="btn btn-primary" onclick={() => submitted = false}>
						Send Another Message
					</button>
				</div>
			{:else}
				<form class="contact-form" onsubmit={handleSubmit}>
					<input type="hidden" name="_subject" value="New contact from JLPT Studio" />
					<input type="text" name="_honey" style="display:none" />
					<div class="form-row">
						<div class="form-group">
							<label for="name">Your Name</label>
							<input id="name" name="name" type="text" placeholder="Tanaka Yuki" required />
						</div>
						<div class="form-group">
							<label for="email">Email Address</label>
							<input id="email" name="email" type="email" placeholder="you@example.com" required />
						</div>
					</div>
					<div class="form-group">
						<label for="subject">Subject</label>
						<select id="subject" name="subject">
							<option value="general">General Inquiry</option>
							<option value="apps">Apps & Features</option>
							<option value="technical">Technical Support</option>
							<option value="partnership">Partnership</option>
						</select>
					</div>
					<div class="form-group">
						<label for="message">Message</label>
						<textarea id="message" name="message" rows="5" placeholder="Tell us how we can help..." required></textarea>
					</div>
					<button type="submit" class="btn btn-primary btn-submit" disabled={submitting}>
						{submitting ? 'Sending...' : 'Send Message'}
						{#if !submitting}
							<svg width="18" height="18" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2.5" stroke-linecap="round" stroke-linejoin="round"><path d="M5 12h14"/><path d="m12 5 7 7-7 7"/></svg>
						{/if}
					</button>
				</form>
			{/if}

			<div class="contact-info">
				<div class="info-card">
					<div class="info-icon">📧</div>
					<h4>Email Us</h4>
					<a href="mailto:mail@jlpt.studio">mail@jlpt.studio</a>
				</div>
				<div class="info-card">
					<div class="info-icon">💬</div>
					<h4>Community</h4>
					<p>Join our Discord for study tips and peer support</p>
				</div>
				<div class="info-card">
					<div class="info-icon">⏰</div>
					<h4>Response Time</h4>
					<p>We typically respond within 24 hours</p>
				</div>
			</div>
		</div>
	</div>
</section>

<style>
	.contact {
		padding: 6rem 1.5rem;
		background: linear-gradient(180deg, #fff 0%, #f0f4ff 100%);
	}

	.container {
		max-width: 1100px;
		margin: 0 auto;
	}

	.section-header {
		text-align: center;
		margin-bottom: 3rem;
	}

	.section-badge {
		display: inline-block;
		background: linear-gradient(135deg, #e8f4f8, #f0e8ff);
		color: #6b5ce7;
		padding: 0.4rem 1rem;
		border-radius: 999px;
		font-size: 0.85rem;
		font-weight: 600;
		margin-bottom: 1rem;
	}

	.section-header h2 {
		font-family: 'Outfit', sans-serif;
		font-size: 2.2rem;
		font-weight: 700;
		color: #1a1a2e;
		margin-bottom: 1rem;
	}

	.section-desc {
		font-size: 1.05rem;
		color: #64748b;
		max-width: 550px;
		margin: 0 auto;
		line-height: 1.7;
	}

	.contact-grid {
		display: grid;
		grid-template-columns: 1.3fr 0.7fr;
		gap: 3rem;
		align-items: start;
	}

	.success-message {
		display: flex;
		flex-direction: column;
		align-items: center;
		justify-content: center;
		text-align: center;
		padding: 3rem 2rem;
		background: white;
		border: 1px solid #e2e8f0;
		border-radius: 16px;
		box-shadow: 0 4px 20px rgba(0, 0, 0, 0.04);
	}

	.success-icon {
		width: 56px;
		height: 56px;
		border-radius: 50%;
		background: linear-gradient(135deg, #6b5ce7, #a78bfa);
		color: white;
		font-size: 1.4rem;
		font-weight: 700;
		display: flex;
		align-items: center;
		justify-content: center;
		margin-bottom: 1.25rem;
	}

	.success-message h3 {
		font-family: 'Outfit', sans-serif;
		font-size: 1.3rem;
		color: #1a1a2e;
		margin-bottom: 0.5rem;
	}

	.success-message p {
		font-size: 0.95rem;
		color: #64748b;
		margin-bottom: 1.5rem;
	}

	.contact-form {
		background: white;
		padding: 2rem;
		border-radius: 16px;
		border: 1px solid #e2e8f0;
		box-shadow: 0 4px 20px rgba(0, 0, 0, 0.04);
	}

	.form-row {
		display: grid;
		grid-template-columns: 1fr 1fr;
		gap: 1rem;
	}

	.form-group {
		margin-bottom: 1.25rem;
	}

	label {
		display: block;
		font-size: 0.8rem;
		font-weight: 600;
		color: #475569;
		letter-spacing: 0.03em;
		text-transform: uppercase;
		margin-bottom: 0.4rem;
	}

	input,
	textarea,
	select {
		width: 100%;
		background: #f8fafc;
		border: 1.5px solid #e2e8f0;
		border-radius: 10px;
		padding: 0.75rem 1rem;
		font-family: 'Inter', sans-serif;
		font-size: 0.95rem;
		color: #1a1a2e;
		transition: all 0.2s ease;
		outline: none;
		box-sizing: border-box;
	}

	input:focus,
	textarea:focus,
	select:focus {
		border-color: #a78bfa;
		background: white;
		box-shadow: 0 0 0 3px rgba(107, 92, 231, 0.08);
	}

	input::placeholder,
	textarea::placeholder {
		color: #94a3b8;
	}

	select {
		appearance: none;
		background-image: url("data:image/svg+xml,%3Csvg xmlns='http://www.w3.org/2000/svg' width='12' height='12' viewBox='0 0 24 24' fill='none' stroke='%2394a3b8' stroke-width='2'%3E%3Cpath d='M6 9l6 6 6-6'/%3E%3C/svg%3E");
		background-repeat: no-repeat;
		background-position: right 1rem center;
		padding-right: 2.5rem;
	}

	textarea {
		resize: vertical;
		min-height: 120px;
	}

	.btn-submit {
		display: inline-flex;
		align-items: center;
		gap: 0.5rem;
		padding: 0.85rem 2rem;
		background: linear-gradient(135deg, #6b5ce7, #a78bfa);
		color: white;
		border: none;
		border-radius: 10px;
		font-family: 'Inter', sans-serif;
		font-size: 0.95rem;
		font-weight: 600;
		cursor: pointer;
		transition: all 0.3s ease;
	}

	.btn-submit:hover {
		transform: translateY(-2px);
		box-shadow: 0 8px 25px rgba(107, 92, 231, 0.3);
	}

	.btn-submit:disabled {
		opacity: 0.6;
		cursor: not-allowed;
		transform: none;
	}

	.contact-info {
		display: flex;
		flex-direction: column;
		gap: 1.25rem;
	}

	.info-card {
		background: white;
		border: 1px solid #e2e8f0;
		border-radius: 14px;
		padding: 1.5rem;
		box-shadow: 0 2px 12px rgba(0, 0, 0, 0.03);
		transition: all 0.3s ease;
	}

	.info-card:hover {
		transform: translateY(-2px);
		box-shadow: 0 6px 20px rgba(0, 0, 0, 0.06);
	}

	.info-icon {
		font-size: 1.5rem;
		margin-bottom: 0.5rem;
	}

	.info-card h4 {
		font-family: 'Outfit', sans-serif;
		font-size: 1rem;
		font-weight: 600;
		color: #1a1a2e;
		margin-bottom: 0.3rem;
	}

	.info-card p,
	.info-card a {
		font-size: 0.9rem;
		color: #64748b;
		text-decoration: none;
		line-height: 1.5;
	}

	.info-card a:hover {
		color: #6b5ce7;
	}

	@media (max-width: 768px) {
		.contact {
			padding: 4rem 1.25rem;
		}

		.section-header h2 {
			font-size: 1.7rem;
		}

		.contact-grid {
			grid-template-columns: 1fr;
			gap: 2rem;
		}

		.form-row {
			grid-template-columns: 1fr;
		}

		.contact-form {
			padding: 1.5rem;
		}
	}
</style>
