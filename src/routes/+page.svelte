<script lang="ts">
	import Nav from '$lib/components/Nav.svelte';
	import Hero from '$lib/components/Hero.svelte';
	import Features from '$lib/components/Features.svelte';
	import HowItWorks from '$lib/components/HowItWorks.svelte';
	import Levels from '$lib/components/Levels.svelte';
	import Testimonials from '$lib/components/Testimonials.svelte';
	import Pricing from '$lib/components/Pricing.svelte';
	import FAQ from '$lib/components/FAQ.svelte';
	import Contact from '$lib/components/Contact.svelte';
	import Footer from '$lib/components/Footer.svelte';
</script>

<svelte:head>
	<title>JLPT Studio — Master the JLPT from N5 to N1</title>
	<meta name="description" content="Master the Japanese Language Proficiency Test with scientifically-backed spaced repetition, kanji mnemonics, and realistic practice exams. From N5 to N1." />
</svelte:head>

<Nav />
<Hero />
<Features />
<HowItWorks />
<Levels />
<Testimonials />
<Pricing />
<FAQ />
<Contact />
<Footer />
