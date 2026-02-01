<script>
	import AstrolinkLogo from '$lib/assets/astrolink.svg';
	import { onMount } from 'svelte';
	const ispTechUsed = [
		'Django',
		'PostgreSQL',
		'TailwindCSS',
		'HTML & CSS',
		'JavaScript',
		'HTMX',
		'Redis',
		'Celery Task Queue',
		'MPESA Daraja API'
	];

	let typedHeading = '';
	const fullHeading = 'Building digital solutions that matter.';

	onMount(() => {
		let i = 0;
		const speed = 60; // ms per character
		const timer = setInterval(() => {
			typedHeading += fullHeading[i];
			i++;
			if (i >= fullHeading.length) clearInterval(timer);
		}, speed);
		return () => clearInterval(timer);
	});
</script>

<svelte:head>
	<title>Borore</title>
	<meta
		name="description"
		content="Personal Portfolio for Moses Borore - Backend Software engineer."
	/>
</svelte:head>
<main class="container mx-auto mt-8 px-4">
	<section
		id="here"
		class="mx-auto flex w-full max-w-7xl flex-col items-center justify-center px-6 py-12 md:px-12 md:py-12"
	>
		<div class="animate-fade-in prose prose-sm mb-6 font-medium prose-slate md:prose-base">
			Welcome to my portfolio
		</div>
		<h1
		class="mb-6 max-w-4xl text-center text-7xl leading-tight font-bold tracking-tighter text-balance lg:text-8xl"
		aria-live="polite"
		>
		{typedHeading}<span class="caret" aria-hidden="true"></span>
	</h1>

		<div class="prose-sm mb-6 font-light">Majorly focused on backend software development.</div>

		<div class="mb-12 flex gap-4">
			<a class="btn btn-primary" href="#projects"> View My Work </a>
			<button class="btn btn-outline btn-secondary"> Get in Touch </button>
		</div>

		<div class="w-full max-w-2xl text-center mb-4">
			<div class="prose-lg text-center font-semibold tracking-wider md:prose-2xl"> Skills</div>
		</div>

		<div
			id="skills"
			class="prose grid w-full max-w-2xl grid-cols-2 gap-8 border-t border-slate-800 pt-8 md:gap-16 prose-p:text-sm"
		>
			<div class="text-center">
				<span class="mb-2 text-3xl font-bold md:text-4xl">4+</span>
				<p>Years Experience</p>
			</div>
			<div class="text-center">
				<span class="mb-2 text-3xl font-bold md:text-4xl">2+</span>
				<p>Years in Consultancy</p>
			</div>
		</div>

		<div class="prose-sm mt-6 max-w-2xl text-center">
			I am a technical consultant who works with companies to quickly diagnose and solve software
			development problems, delivering solutions that are practical, scalable, and aligned with
			business goals. I bridge the gap between technical teams and non-technical stakeholders,
			making complex systems easier to understand and decisions easier to make.
		</div>
	</section>
	<div class="flex animate-bounce justify-center text-center prose-slate">
		<svg class="h-6 w-6" fill="none" stroke="currentColor" viewBox="0 0 24 24">
			<path
				stroke-linecap="round"
				stroke-linejoin="round"
				stroke-width="2"
				d="M19 14l-7 7m0 0l-7-7m7 7V3"
			/>
		</svg>
	</div>
	<section id="projects" class="mx-auto my-4 prose max-w-2xl space-y-8">
		<h3 class="prose-lg text-center font-semibold tracking-wider md:prose-2xl">
			Featured Projects
		</h3>

		<div id="projectList">
			<div class="card">
				<div class="prose card-body p-4">
					<div class="flex items-center gap-4">
						<img
							src={AstrolinkLogo}
							alt="Astrolink Logo"
							class="prose size-25 prose-img:object-cover"
						/>

						<div>
							<h4 class="card-title">Astrolink</h4>
							<p class="prose- text-xs">
								ISP billing and hotspot management system that integrates MikroTik, FreeRADIUS, and
								M-Pesa to automate user authentication, payments, and internet access control.
							</p>
						</div>
					</div>

					<div class="collapse-arrow collapse w-full">
						<input type="checkbox" />
						<div class="collapse-title prose-sm p-2 font-semibold text-base-content">Details</div>
						<div class="collapse-content space-y-4 text-sm">
							<div>
								<span class="prose prose-sm font-semibold">Technologies used:</span>
								<div class="mt-4 flex flex-wrap gap-2">
									{#each ispTechUsed as techUsed}
										<button class="btn rounded-lg p-1 text-xs btn-soft btn-sm">{techUsed}</button>
									{/each}
								</div>
							</div>

							<span class="prose prose-sm mb-2 block font-semibold">Challenges & Learnings</span>
							<div class="join join-vertical w-full bg-base-200/80">
								<div class="collapse-arrow collapse join-item border border-base-300">
									<input type="checkbox" name="my-accordion-223" />
									<div class="collapse-title text-sm font-semibold">
										Payment status monitoring and automatic plan activation
                    
									</div>
									<div class="collapse-content text-xs">
										I didn't want to send the user to a different page to manually activate the
										chosen plan upon, hopefully, a successful payment. To ensured minimal user
										interaction during purchasing and activation process, the frontend actively
										monitors the payment status by polling the backend. If successful, we
										automatically purchase the plan and activate it. Else redirect the user to the
										failed payment page.
									</div>
								</div>
								<div class="collapse-arrow collapse join-item border border-base-300">
									<input type="checkbox" name="my-accordion-2" />
									<div class="stext-sm collapse-title font-semibold">
										Wallet integrity & Audit trail
									</div>
									<div class="collapse-content text-xs">
										Crediting and debiting the user's wallet is simple and easy to implement. But,
										it is not the best way to handle transactions within the system that requires to
										maintain wallet integrity and audit trail. For provision of audit trail, I added
										a ledger table that every user wallet should have. The ledger table records
										every transaction (interaction to add or deduct wallet balance) involving the
										user's wallet. For integrity, every addition or deduction of the wallet balance
										occurred inside a transaction.
									</div>
								</div>
							</div>

							<a
								href="https://github.com/mosesborore/isp-management-system"
								class="btn rounded-2xl btn-sm btn-accent">Check it out</a
							>
						</div>
					</div>
				</div>
			</div>
		</div>
	</section>
	<section id="tools" class="mx-auto my-4 prose max-w-2xl space-y-8">
		<h3 class="prose-lg text-center font-semibold tracking-wider md:prose-2xl">Tools</h3>

		<div class="grid grid-cols-3 gap-4 prose-li:text-xs">
			<div id="frontendTools">
				<h4 class="indent-8 font-semibold">Frontend</h4>
				<ul class="list-none">
					<li>HTML, JavaScript & CSS</li>
					<li>TailwindCSS</li>
					<li>Svelte & SvelteKit</li>
					<li>HTMX</li>
				</ul>
			</div>

			<div id="backendTools">
				<h4 class="prose indent-8 font-semibold">Backend</h4>
				<ul class="list-none">
					<li>Django</li>
					<li>PostgreSQL</li>
					<li>NodeJS</li>
					<li>Redis</li>
					<li>Celery</li>
				</ul>
			</div>
			<div id="otherTools">
				<h4 class="prose indent-8 font-semibold">Other Tools</h4>
				<ul class="list-none">
					<li>MPESA via Daraja API</li>
					<li>Docker</li>
				</ul>
			</div>
		</div>
	</section>
</main>

	<style>
	/* Typewriter caret */
	@keyframes blink { 0%, 50% { opacity: 1 } 50.01%, 100% { opacity: 0 } }
	.caret {
		display: inline-block;
		width: 2px;
		height: 1em;
		background: currentColor;
		margin-left: 6px;
		vertical-align: text-bottom;
		animation: blink 1s step-start infinite;
	}
	</style>
