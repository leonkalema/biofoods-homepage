<script lang="ts">
	import { onMount } from 'svelte';

	let mounted = false;

	onMount(() => {
		mounted = true;
	});
</script>

<svelte:head>
	<title>BioFoods Website Proposal | Next-Gen Digital Platform</title>
	<meta name="description" content="Professional proposal for BioFoods' award-winning website redesign - East Africa's leading sustainable dairy company." />
</svelte:head>

<div class="min-h-screen bg-gradient-to-br from-slate-50 to-white">
	<!-- Header -->
	<header class="bg-white border-b border-gray-200">
		<div class="max-w-4xl mx-auto px-6 py-16 text-center">
			<div class="mb-8">
				<img src="/bio-logo-no-strapline-2020.png" alt="BioFoods Logo" class="h-20 mx-auto mb-6" />
			</div>
			<h1 class="text-4xl font-bold text-gray-900 mb-4">Website Development Proposal</h1>
			<p class="text-lg text-gray-600 mb-8 max-w-2xl mx-auto">
				Comprehensive digital solution for BioFoods - Kenya's leading B-Corp certified dairy company
			</p>
			<div class="grid grid-cols-1 md:grid-cols-3 gap-6 max-w-3xl mx-auto">
				<div class="flex flex-col items-center p-4">
					<div class="w-12 h-12 bg-blue-100 rounded-full flex items-center justify-center mb-3">
						<svg class="w-6 h-6 text-blue-600" fill="none" stroke="currentColor" viewBox="0 0 24 24">
							<path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M9 12l2 2 4-4m6 2a9 9 0 11-18 0 9 9 0 0118 0z"></path>
						</svg>
					</div>
					<h3 class="font-semibold text-gray-900 mb-1">Professional Design</h3>
					<p class="text-sm text-gray-600 text-center">Modern, responsive design</p>
				</div>
				<div class="flex flex-col items-center p-4">
					<div class="w-12 h-12 bg-green-100 rounded-full flex items-center justify-center mb-3">
						<svg class="w-6 h-6 text-green-600" fill="none" stroke="currentColor" viewBox="0 0 24 24">
							<path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M13 10V3L4 14h7v7l9-11h-7z"></path>
						</svg>
					</div>
					<h3 class="font-semibold text-gray-900 mb-1">Fast Performance</h3>
					<p class="text-sm text-gray-600 text-center">Optimized for speed</p>
				</div>
				<div class="flex flex-col items-center p-4">
					<div class="w-12 h-12 bg-purple-100 rounded-full flex items-center justify-center mb-3">
						<svg class="w-6 h-6 text-purple-600" fill="none" stroke="currentColor" viewBox="0 0 24 24">
							<path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M12 15v2m-6 4h12a2 2 0 002-2v-6a2 2 0 00-2-2H6a2 2 0 00-2 2v6a2 2 0 002 2zm10-10V7a4 4 0 00-8 0v4h8z"></path>
						</svg>
					</div>
					<h3 class="font-semibold text-gray-900 mb-1">Secure & Reliable</h3>
					<p class="text-sm text-gray-600 text-center">Enterprise-grade security</p>
				</div>
			</div>
		</div>
	</header>

	<!-- Main Content -->
	<main class="max-w-4xl mx-auto px-6 py-16">
		<div class="space-y-32">
		
		<!-- Introduction -->
		<section class="prose prose-lg max-w-none mt-16" class:opacity-0={!mounted} class:animate-fade-in={mounted}>
			<div class="bg-white rounded-2xl p-8 shadow-sm border border-slate-200">
				<h2 class="text-4xl font-light text-slate-900 mb-6">Hi! I Think I Know U.</h2>
				<p class="text-slate-700 leading-relaxed text-lg">
					Bio Foods Ltd is an East-African pioneer in health-first, sustainable dairy. Your next-gen website must mirror that leadership: immersive storytelling, data-driven insights, and friction-free journeys for consumers and trade partners. We will deliver a modular, lightning-fast digital platform, built on a headless architecture that empowers your team to spin up campaign microsites in minutes, drives measurable engagement, and future-proofs the brand for global expansion.
				</p>
			</div>
		</section>

		<!-- Current State -->
		<section class="prose prose-lg max-w-none" class:opacity-0={!mounted} class:animate-fade-in-delay={mounted}>
			<div class="bg-white rounded-2xl p-8 shadow-sm border border-slate-200">
				<h2 class="text-4xl font-light text-slate-900 mb-6">Where We Are</h2>
				<div class="space-y-4">
					<p class="text-slate-600 mb-4">Current challenges:</p>
					<ul class="space-y-2 text-slate-700">
						<li>• Limited backend flexibility, slow mobile performance</li>
						<li>• Inconsistent content formatting, and no audience segmentation</li>
					</ul>
					<p class="text-slate-600 mt-6 mb-4">Desired outcome: a <strong>"WOW"</strong> site that:</p>
					<ul class="space-y-2 text-slate-700">
						<li>• Showcases Bio Foods' B-Corp story, product innovation & impact</li>
						<li>• Serves B2C and B2B/Export with tailored pathways</li>
						<li>• Enables rapid campaign launches without developers</li>
						<li>• Delivers actionable analytics & SEO lift</li>
						<li>• Meets WCAG 2.1 AA and GDPR/Kenya Data P. regs</li>
					</ul>
				</div>
			</div>
		</section>

		<!-- Solution -->
		<section class="prose prose-lg max-w-none" class:opacity-0={!mounted} class:animate-fade-in-delay-2={mounted}>
			<div class="bg-white rounded-2xl p-8 shadow-sm border border-slate-200">
				<h2 class="text-4xl font-light text-slate-900 mb-6">Where To Go</h2>
				<p class="text-slate-600 mb-6">How before Where and Why.</p>
				<div class="grid grid-cols-1 md:grid-cols-2 gap-6">
					<div class="space-y-4">
						<div class="p-4 bg-slate-50 rounded-lg">
							<h3 class="font-medium text-slate-900">Great Experience</h3>
							<p class="text-sm text-slate-600 mt-1">Cinematic storytelling with award-worthy design</p>
						</div>
						<div class="p-4 bg-slate-50 rounded-lg">
							<h3 class="font-medium text-slate-900">Scalability</h3>
							<p class="text-sm text-slate-600 mt-1">Headless CMS for rapid content deployment</p>
						</div>
					</div>
					<div class="space-y-4">
						<div class="p-4 bg-slate-50 rounded-lg">
							<h3 class="font-medium text-slate-900">Conversion</h3>
							<p class="text-sm text-slate-600 mt-1">Tailored B2C/B2B journeys with analytics</p>
						</div>
						<div class="p-4 bg-slate-50 rounded-lg">
							<h3 class="font-medium text-slate-900">Long-standing tech</h3>
							<p class="text-sm text-slate-600 mt-1">Future-proof architecture like your brand</p>
						</div>
					</div>
				</div>
			</div>
		</section>

		<!-- Project Roadmap -->
		<section class="prose prose-lg max-w-none" class:opacity-0={!mounted} class:animate-fade-in-delay-3={mounted}>
			<div class="bg-white rounded-2xl p-8 shadow-sm border border-slate-200">
				<h2 class="text-4xl font-light text-slate-900 mb-6">Project Roadmap</h2>
				<div class="space-y-4">
					<ul class="space-y-3 text-slate-700">
						<li class="flex items-center space-x-3">
							<span class="w-2 h-2 bg-emerald-500 rounded-full"></span>
							<span>Research</span>
						</li>
						<li class="flex items-center space-x-3">
							<span class="w-2 h-2 bg-emerald-500 rounded-full"></span>
							<span>Design</span>
						</li>
						<li class="flex items-center space-x-3">
							<span class="w-2 h-2 bg-emerald-500 rounded-full"></span>
							<span>Develop</span>
						</li>
						<li class="flex items-center space-x-3">
							<span class="w-2 h-2 bg-emerald-500 rounded-full"></span>
							<span>Test</span>
						</li>
						<li class="flex items-center space-x-3">
							<span class="w-2 h-2 bg-emerald-500 rounded-full"></span>
							<span>Deploy</span>
						</li>
					</ul>
					<div class="mt-8 p-6 bg-emerald-50 rounded-lg border border-emerald-200">
						<h3 class="text-2xl font-light text-emerald-900">4 Weeks</h3>
						<p class="text-emerald-700 mt-1">Complete delivery timeline</p>
					</div>
				</div>
			</div>
		</section>

		<!-- Technology Stack -->
		<section class="prose prose-lg max-w-none" class:opacity-0={!mounted} class:animate-fade-in-delay-4={mounted}>
			<div class="bg-white rounded-2xl p-8 shadow-sm border border-slate-200">
				<h2 class="text-4xl font-light text-slate-900 mb-6">Technology Stack</h2>
				<div class="grid grid-cols-1 md:grid-cols-2 gap-8">
					<div class="space-y-4">
						<h3 class="text-lg font-medium text-slate-900">Frontend</h3>
						<ul class="space-y-2 text-slate-700 text-sm">
							<li>• SvelteKit v2, TypeScript, Tailwind CSS</li>
							<li>• GSAP / Motion for animations</li>
						</ul>
						
						<h3 class="text-lg font-medium text-slate-900 mt-6">CMS</h3>
						<ul class="space-y-2 text-slate-700 text-sm">
							<li>• Contentful (headless, GraphQL & REST)</li>
						</ul>

						<h3 class="text-lg font-medium text-slate-900 mt-6">Hosting</h3>
						<ul class="space-y-2 text-slate-700 text-sm">
							<li>• Netlify Edge Network with branch previews & global CDN</li>
						</ul>
					</div>
					<div class="space-y-4">
						<h3 class="text-lg font-medium text-slate-900">Forms & Data</h3>
						<ul class="space-y-2 text-slate-700 text-sm">
							<li>• Supabase (Postgres + Edge Functions) for gated downloads & trade leads</li>
						</ul>

						<h3 class="text-lg font-medium text-slate-900 mt-6">Search & Personalisation</h3>
						<ul class="space-y-2 text-slate-700 text-sm">
							<li>• Algolia (or Supabase Edge search)</li>
						</ul>

						<h3 class="text-lg font-medium text-slate-900 mt-6">Analytics</h3>
						<ul class="space-y-2 text-slate-700 text-sm">
							<li>• GA4, Netlify Analytics, Meta Pixel, Hotjar</li>
							<li>• Custom Looker Studio KPI dashboard</li>
						</ul>

						<h3 class="text-lg font-medium text-slate-900 mt-6">Compliance</h3>
						<ul class="space-y-2 text-slate-700 text-sm">
							<li>• Cookiebot, ISO 27001-cert infrastructure</li>
							<li>• WCAG plugin</li>
						</ul>
					</div>
				</div>
			</div>
		</section>

		<!-- Project Investment -->
		<section class="prose prose-lg max-w-none" class:opacity-0={!mounted} class:animate-fade-in-delay-5={mounted}>
			<div class="bg-gradient-to-br from-slate-900 via-slate-800 to-slate-900 rounded-3xl p-12 shadow-2xl border border-slate-700 relative overflow-hidden">
				<!-- Enhanced Background decoration -->
				<div class="absolute top-0 right-0 w-40 h-40 bg-gradient-to-br from-emerald-400/20 to-emerald-600/20 rounded-full blur-xl -translate-y-20 translate-x-20"></div>
				<div class="absolute bottom-0 left-0 w-32 h-32 bg-gradient-to-br from-blue-400/20 to-blue-600/20 rounded-full blur-xl translate-y-16 -translate-x-16"></div>
				<div class="absolute top-1/2 left-1/2 w-24 h-24 bg-gradient-to-br from-purple-400/10 to-purple-600/10 rounded-full blur-xl -translate-x-12 -translate-y-12"></div>
				
				<div class="relative z-10">
					<div class="text-center mb-12">
						<h2 class="text-5xl font-light text-white mb-4">Project Investment</h2>
						<p class="text-slate-300 text-lg max-w-2xl mx-auto">Enterprise-grade digital transformation with measurable ROI for BioFoods</p>
					</div>
					
					<div class="grid grid-cols-1 lg:grid-cols-2 gap-8 mb-12">
						<!-- Primary Package -->
						<div class="relative">
							<div class="absolute -inset-1 bg-gradient-to-r from-emerald-500 to-blue-500 rounded-3xl blur opacity-25"></div>
							<div class="relative p-8 bg-white rounded-2xl shadow-xl border border-slate-200">
								<div class="flex items-center justify-between mb-6">
									<div>
										<h3 class="text-2xl font-semibold text-slate-900">Complete Digital Platform</h3>
										<p class="text-slate-600 text-sm mt-1">Full-service website development</p>
									</div>
									<div class="w-14 h-14 bg-gradient-to-br from-emerald-500 to-emerald-600 rounded-full flex items-center justify-center shadow-lg">
										<svg class="w-7 h-7 text-white" fill="none" stroke="currentColor" viewBox="0 0 24 24">
											<path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M13 10V3L4 14h7v7l9-11h-7z"></path>
										</svg>
									</div>
								</div>
								<div class="mb-8">
									<div class="flex items-baseline space-x-2">
										<span class="text-5xl font-light text-slate-900">KES 320,000</span>
										<span class="text-slate-500 text-lg">one-time</span>
									</div>
									<div class="mt-2 flex items-center space-x-2">
										<span class="text-sm text-emerald-600 bg-emerald-50 px-3 py-1 rounded-full font-medium">Best Value</span>
										<span class="text-sm text-slate-500">~$2,400 USD</span>
									</div>
								</div>
								<div class="space-y-4">
									<div class="flex items-start space-x-3">
										<div class="w-2 h-2 bg-emerald-500 rounded-full mt-2 flex-shrink-0"></div>
										<div>
											<span class="text-slate-900 font-medium">Award-worthy design system</span>
											<p class="text-slate-600 text-sm mt-1">Custom UI components & brand guidelines</p>
										</div>
									</div>
									<div class="flex items-start space-x-3">
										<div class="w-2 h-2 bg-emerald-500 rounded-full mt-2 flex-shrink-0"></div>
										<div>
											<span class="text-slate-900 font-medium">10+ responsive page templates</span>
											<p class="text-slate-600 text-sm mt-1">Homepage, products, about, contact & more</p>
										</div>
									</div>
									<div class="flex items-start space-x-3">
										<div class="w-2 h-2 bg-emerald-500 rounded-full mt-2 flex-shrink-0"></div>
										<div>
											<span class="text-slate-900 font-medium">Dual B2C/B2B user journeys</span>
											<p class="text-slate-600 text-sm mt-1">Tailored experiences for different audiences</p>
										</div>
									</div>
									<div class="flex items-start space-x-3">
										<div class="w-2 h-2 bg-emerald-500 rounded-full mt-2 flex-shrink-0"></div>
										<div>
											<span class="text-slate-900 font-medium">Headless CMS integration</span>
											<p class="text-slate-600 text-sm mt-1">Easy content management + team training</p>
										</div>
									</div>
									<div class="flex items-start space-x-3">
										<div class="w-2 h-2 bg-emerald-500 rounded-full mt-2 flex-shrink-0"></div>
										<div>
											<span class="text-slate-900 font-medium">Performance optimization</span>
											<p class="text-slate-600 text-sm mt-1">Sub-2s load times, SEO optimization</p>
										</div>
									</div>
									<div class="flex items-start space-x-3">
										<div class="w-2 h-2 bg-emerald-500 rounded-full mt-2 flex-shrink-0"></div>
										<div>
											<span class="text-slate-900 font-medium">Analytics & compliance</span>
											<p class="text-slate-600 text-sm mt-1">GDPR/Kenya Data Protection ready</p>
										</div>
									</div>
								</div>
							</div>
						</div>
						
						<!-- Hosting Package -->
						<div class="p-8 bg-slate-800/50 backdrop-blur-sm rounded-2xl border border-slate-600 shadow-xl">
							<div class="flex items-center justify-between mb-6">
								<div>
									<h3 class="text-2xl font-semibold text-white">Enterprise Hosting</h3>
									<p class="text-slate-300 text-sm mt-1">Premium infrastructure & support</p>
								</div>
								<div class="w-14 h-14 bg-gradient-to-br from-blue-500 to-blue-600 rounded-full flex items-center justify-center shadow-lg">
									<svg class="w-7 h-7 text-white" fill="none" stroke="currentColor" viewBox="0 0 24 24">
										<path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M5 12h14M5 12l4-4m-4 4l4 4"></path>
									</svg>
								</div>
							</div>
							<div class="mb-8">
								<div class="flex items-baseline space-x-2">
									<span class="text-5xl font-light text-white">KES 20,000</span>
									<span class="text-slate-300 text-lg">annually</span>
								</div>
								<div class="mt-2 flex items-center space-x-2">
									<span class="text-sm text-blue-400 bg-blue-900/30 px-3 py-1 rounded-full font-medium">Enterprise</span>
									<span class="text-sm text-slate-400">~$150 USD/year</span>
								</div>
							</div>
							<div class="space-y-4">
								<div class="flex items-start space-x-3">
									<div class="w-2 h-2 bg-blue-400 rounded-full mt-2 flex-shrink-0"></div>
									<div>
										<span class="text-white font-medium">Global CDN & hosting</span>
										<p class="text-slate-300 text-sm mt-1">Lightning-fast worldwide delivery</p>
									</div>
								</div>
								<div class="flex items-start space-x-3">
									<div class="w-2 h-2 bg-blue-400 rounded-full mt-2 flex-shrink-0"></div>
									<div>
										<span class="text-white font-medium">SSL & enterprise security</span>
										<p class="text-slate-300 text-sm mt-1">Bank-grade encryption & protection</p>
									</div>
								</div>
								<div class="flex items-start space-x-3">
									<div class="w-2 h-2 bg-blue-400 rounded-full mt-2 flex-shrink-0"></div>
									<div>
										<span class="text-white font-medium">24/7 monitoring & support</span>
										<p class="text-slate-300 text-sm mt-1">Proactive maintenance & updates</p>
									</div>
								</div>
								<div class="flex items-start space-x-3">
									<div class="w-2 h-2 bg-blue-400 rounded-full mt-2 flex-shrink-0"></div>
									<div>
										<span class="text-white font-medium">99.9% uptime SLA</span>
										<p class="text-slate-300 text-sm mt-1">Guaranteed availability & performance</p>
									</div>
								</div>
							</div>
						</div>
					</div>
					
					<!-- ROI & Timeline Section -->
					<div class="grid grid-cols-1 md:grid-cols-3 gap-6 mb-8">
						<div class="text-center p-6 bg-white/10 backdrop-blur-sm rounded-xl border border-white/20">
							<div class="w-12 h-12 bg-emerald-500/20 rounded-full flex items-center justify-center mx-auto mb-4">
								<svg class="w-6 h-6 text-emerald-400" fill="none" stroke="currentColor" viewBox="0 0 24 24">
									<path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M13 7h8m0 0v8m0-8l-8 8-4-4-6 6"></path>
								</svg>
							</div>
							<h4 class="text-lg font-semibold text-white mb-2">Expected ROI</h4>
							<p class="text-2xl font-bold text-emerald-400 mb-1">300%+</p>
							<p class="text-slate-300 text-sm">Within 12 months</p>
						</div>
						<div class="text-center p-6 bg-white/10 backdrop-blur-sm rounded-xl border border-white/20">
							<div class="w-12 h-12 bg-blue-500/20 rounded-full flex items-center justify-center mx-auto mb-4">
								<svg class="w-6 h-6 text-blue-400" fill="none" stroke="currentColor" viewBox="0 0 24 24">
									<path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M12 8v4l3 3m6-3a9 9 0 11-18 0 9 9 0 0118 0z"></path>
								</svg>
							</div>
							<h4 class="text-lg font-semibold text-white mb-2">Delivery Timeline</h4>
							<p class="text-2xl font-bold text-blue-400 mb-1">3-5 weeks</p>
							<p class="text-slate-300 text-sm">From project start</p>
						</div>
						<div class="text-center p-6 bg-white/10 backdrop-blur-sm rounded-xl border border-white/20">
							<div class="w-12 h-12 bg-purple-500/20 rounded-full flex items-center justify-center mx-auto mb-4">
								<svg class="w-6 h-6 text-purple-400" fill="none" stroke="currentColor" viewBox="0 0 24 24">
									<path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M9 12l2 2 4-4m5.618-4.016A11.955 11.955 0 0112 2.944a11.955 11.955 0 01-8.618 3.04A12.02 12.02 0 003 9c0 5.591 3.824 10.29 9 11.622 5.176-1.332 9-6.03 9-11.622 0-1.042-.133-2.052-.382-3.016z"></path>
								</svg>
							</div>
							<h4 class="text-lg font-semibold text-white mb-2">Warranty</h4>
							<p class="text-2xl font-bold text-purple-400 mb-1">12 months</p>
							<p class="text-slate-300 text-sm">Full support included</p>
						</div>
					</div>
					
					<!-- Payment Terms -->
					<div class="bg-white/5 backdrop-blur-sm rounded-xl p-6 border border-white/10">
						<h4 class="text-lg font-semibold text-white mb-4">Flexible Payment Terms</h4>
						<div class="grid grid-cols-1 md:grid-cols-2 gap-6">
							<div class="flex items-center space-x-4">
								<div class="w-8 h-8 bg-emerald-500/20 rounded-full flex items-center justify-center flex-shrink-0">
									<span class="text-emerald-400 font-semibold text-sm">1</span>
								</div>
								<div>
									<p class="text-white font-medium">50% deposit to start</p>
									<p class="text-slate-300 text-sm">KES 160,000 upon contract signing</p>
								</div>
							</div>
							<div class="flex items-center space-x-4">
								<div class="w-8 h-8 bg-blue-500/20 rounded-full flex items-center justify-center flex-shrink-0">
									<span class="text-blue-400 font-semibold text-sm">2</span>
								</div>
								<div>
									<p class="text-white font-medium">50% on completion</p>
									<p class="text-slate-300 text-sm">KES 160,000 upon project delivery</p>
								</div>
							</div>
						</div>
					</div>
				</div>
			</div>
		</section>

		<!-- Portfolio Section -->
		<section class="prose prose-lg max-w-none mt-16" class:opacity-0={!mounted} class:animate-fade-in-delay-3={mounted}>
			<div class="bg-white border-b border-gray-200 py-16">
				<div class="max-w-4xl mx-auto text-center px-6">
					<div class="mb-8">
						<img src="/bio-logo-no-strapline-2020.png" alt="BioFoods Logo" class="h-20 mx-auto mb-6" />
					</div>
					<h1 class="text-4xl font-bold text-gray-900 mb-4">Website Development Proposal</h1>
					<p class="text-lg text-gray-600 mb-8 max-w-2xl mx-auto">
						Comprehensive digital transformation for Kenya's leading B-Corp certified dairy company
					</p>
					<div class="grid grid-cols-1 md:grid-cols-2 lg:grid-cols-4 gap-6 mb-12">
						<div class="bg-white rounded-lg p-6 shadow-sm border border-gray-200 hover:shadow-md transition-shadow">
							<div class="w-12 h-12 bg-red-100 rounded-lg flex items-center justify-center mb-4">
								<svg class="w-6 h-6 text-red-600" fill="none" stroke="currentColor" viewBox="0 0 24 24">
									<path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M21 12a9 9 0 01-9 9m9-9a9 9 0 00-9-9m9 9H3m9 9v-9m0-9v9"></path>
								</svg>
							</div>
							<h3 class="text-lg font-semibold text-gray-900 mb-2">Strawberry.se</h3>
							<p class="text-sm text-gray-600 mb-3">Swedish Market Leader</p>
							<a href="https://www.strawberry.se/" target="_blank" class="text-blue-600 text-sm hover:text-blue-800 transition-colors">
								View Website →
							</a>
						</div>
						
						<div class="bg-white rounded-lg p-6 shadow-sm border border-gray-200 hover:shadow-md transition-shadow">
							<div class="w-12 h-12 bg-green-100 rounded-lg flex items-center justify-center mb-4">
								<svg class="w-6 h-6 text-green-600" fill="none" stroke="currentColor" viewBox="0 0 24 24">
									<path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M3.055 11H5a2 2 0 012 2v1a2 2 0 002 2 2 2 0 012 2v2.945M8 3.935V5.5A2.5 2.5 0 0010.5 8h.5a2 2 0 012 2 2 2 0 104 0 2 2 0 012-2h1.064M15 20.488V18a2 2 0 012-2h3.064M21 12a9 9 0 11-18 0 9 9 0 0118 0z"></path>
								</svg>
							</div>
							<h3 class="text-lg font-semibold text-gray-900 mb-2">Dream Kenya Safaris</h3>
							<p class="text-sm text-gray-600 mb-3">Tourism & Hospitality</p>
							<a href="https://dreamkenyasafaris.com/" target="_blank" class="text-blue-600 text-sm hover:text-blue-800 transition-colors">
								View Website →
							</a>
						</div>
						
						<div class="bg-white rounded-lg p-6 shadow-sm border border-gray-200 hover:shadow-md transition-shadow">
							<div class="w-12 h-12 bg-orange-100 rounded-lg flex items-center justify-center mb-4">
								<svg class="w-6 h-6 text-orange-600" fill="none" stroke="currentColor" viewBox="0 0 24 24">
									<path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M12 6.253v13m0-13C10.832 5.477 9.246 5 7.5 5S4.168 5.477 3 6.253v13C4.168 18.477 5.754 18 7.5 18s3.332.477 4.5 1.253m0-13C13.168 5.477 14.754 5 16.5 5c1.747 0 3.332.477 4.5 1.253v13C19.832 18.477 18.247 18 16.5 18c-1.746 0-3.332.477-4.5 1.253"></path>
								</svg>
							</div>
							<h3 class="text-lg font-semibold text-gray-900 mb-2">Ma Cuisine</h3>
							<p class="text-sm text-gray-600 mb-3">Food & Beverage</p>
							<a href="https://macuisine.co.ke/" target="_blank" class="text-blue-600 text-sm hover:text-blue-800 transition-colors">
								View Website →
							</a>
						</div>
						
						<div class="bg-white rounded-lg p-6 shadow-sm border border-gray-200 hover:shadow-md transition-shadow">
							<div class="w-12 h-12 bg-blue-100 rounded-lg flex items-center justify-center mb-4">
								<svg class="w-6 h-6 text-blue-600" fill="none" stroke="currentColor" viewBox="0 0 24 24">
									<path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M4.318 6.318a4.5 4.5 0 000 6.364L12 20.364l7.682-7.682a4.5 4.5 0 00-6.364-6.364L12 7.636l-1.318-1.318a4.5 4.5 0 00-6.364 0z"></path>
								</svg>
							</div>
							<h3 class="text-lg font-semibold text-gray-900 mb-2">Coral Spirit</h3>
							<p class="text-sm text-gray-600 mb-3">Lifestyle & Wellness</p>
							<a href="https://coralspirit.com/" target="_blank" class="text-blue-600 text-sm hover:text-blue-800 transition-colors">
								View Website →
							</a>
						</div>
					</div>
					
					<div class="flex flex-wrap justify-center gap-8 text-gray-600">
						<div class="flex items-center space-x-2">
							<svg class="w-5 h-5 text-green-600" fill="none" stroke="currentColor" viewBox="0 0 24 24">
								<path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M9 12l2 2 4-4m6 2a9 9 0 11-18 0 9 9 0 0118 0z"></path>
							</svg>
							<span>International Experience</span>
						</div>
						<div class="flex items-center space-x-2">
							<svg class="w-5 h-5 text-green-600" fill="none" stroke="currentColor" viewBox="0 0 24 24">
								<path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M9 12l2 2 4-4m6 2a9 9 0 11-18 0 9 9 0 0118 0z"></path>
							</svg>
							<span>Food & Beverage Expertise</span>
						</div>
						<div class="flex items-center space-x-2">
							<svg class="w-5 h-5 text-green-600" fill="none" stroke="currentColor" viewBox="0 0 24 24">
								<path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M9 12l2 2 4-4m6 2a9 9 0 11-18 0 9 9 0 0118 0z"></path>
							</svg>
							<span>Kenyan Market Knowledge</span>
						</div>
					</div>
				</div>
			</div>
		</section>

		<!-- Call to Action -->
		<section class="prose prose-lg max-w-none" class:opacity-0={!mounted} class:animate-fade-in-delay-6={mounted}>
			<div class="relative bg-gradient-to-br from-emerald-600 via-emerald-700 to-emerald-800 py-24 px-8 text-center text-white overflow-hidden">
				<!-- Background Pattern -->
				<div class="absolute inset-0 opacity-10">
					<div class="absolute top-0 left-0 w-full h-full" style="background-image: url('data:image/svg+xml,%3Csvg width=%2760%27 height=%2760%27 viewBox=%270 0 60 60%27 xmlns=%27http://www.w3.org/2000/svg%27%3E%3Cg fill=%27none%27 fill-rule=%27evenodd%27%3E%3Cg fill=%27%23ffffff%27 fill-opacity=%270.1%27%3E%3Ccircle cx=%2730%27 cy=%2730%27 r=%272%27/%3E%3C/g%3E%3C/g%3E%3C/svg%3E')"></div>
				</div>
				
				<!-- Floating Elements -->
				<div class="absolute top-10 left-10 w-20 h-20 bg-white/5 rounded-full blur-xl"></div>
				<div class="absolute bottom-10 right-10 w-32 h-32 bg-white/5 rounded-full blur-xl"></div>
				<div class="absolute top-1/2 right-1/4 w-16 h-16 bg-white/5 rounded-full blur-xl"></div>
				
				<div class="relative z-10 max-w-4xl mx-auto">
					<div class="mb-8">
						<div class="inline-flex items-center px-4 py-2 bg-white/10 backdrop-blur-sm rounded-full border border-white/20 mb-6">
							<svg class="w-5 h-5 text-emerald-300 mr-2" fill="none" stroke="currentColor" viewBox="0 0 24 24">
								<path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M13 10V3L4 14h7v7l9-11h-7z"></path>
							</svg>
							<span class="text-white font-medium text-sm">Ready to Transform Your Digital Presence?</span>
						</div>
						<h2 class="text-5xl md:text-6xl font-light text-white mb-6 leading-tight">
							Let's Build Something 
							<span class="bg-gradient-to-r from-white to-emerald-100 bg-clip-text text-transparent font-semibold">Extraordinary</span>
						</h2>
						<p class="text-emerald-100 mb-12 max-w-3xl mx-auto text-xl leading-relaxed">
							Transform BioFoods into a digital leader with an award-winning website that drives measurable growth, showcases your B-Corp values, and delivers exceptional user experiences across all touchpoints.
						</p>
					</div>
					
					<!-- Action Buttons -->
					<div class="flex flex-col sm:flex-row gap-6 justify-center mb-12">
						<a href="mailto:leon@example.com" class="group relative inline-flex items-center justify-center px-8 py-4 bg-white text-emerald-700 rounded-xl font-semibold text-lg shadow-xl hover:shadow-2xl transition-all duration-300 hover:scale-105">
							<svg class="w-5 h-5 mr-2 group-hover:rotate-12 transition-transform duration-300" fill="none" stroke="currentColor" viewBox="0 0 24 24">
								<path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M3 8l7.89 4.26a2 2 0 002.22 0L21 8M5 19h14a2 2 0 002-2V7a2 2 0 00-2-2H5a2 2 0 00-2 2v10a2 2 0 002 2z"></path>
							</svg>
							Start Your Project
							<div class="absolute inset-0 bg-gradient-to-r from-emerald-50 to-white rounded-xl opacity-0 group-hover:opacity-100 transition-opacity duration-300 -z-10"></div>
						</a>
						<a href="/" class="group inline-flex items-center justify-center px-8 py-4 border-2 border-white/30 text-white rounded-xl font-semibold text-lg backdrop-blur-sm hover:bg-white/10 hover:border-white/50 transition-all duration-300">
							<svg class="w-5 h-5 mr-2 group-hover:scale-110 transition-transform duration-300" fill="none" stroke="currentColor" viewBox="0 0 24 24">
								<path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M15 12a3 3 0 11-6 0 3 3 0 016 0z"></path>
								<path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M2.458 12C3.732 7.943 7.523 5 12 5c4.478 0 8.268 2.943 9.542 7-1.274 4.057-5.064 7-9.542 7-4.477 0-8.268-2.943-9.542-7z"></path>
							</svg>
							View Live Demo
						</a>
					</div>
					
					<!-- Trust Indicators -->
					<div class="grid grid-cols-1 md:grid-cols-3 gap-8 max-w-4xl mx-auto">
						<div class="text-center p-6 bg-white/5 backdrop-blur-sm rounded-xl border border-white/10">
							<div class="w-12 h-12 bg-white/10 rounded-full flex items-center justify-center mx-auto mb-4">
								<svg class="w-6 h-6 text-white" fill="none" stroke="currentColor" viewBox="0 0 24 24">
									<path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M12 15v2m-6 4h12a2 2 0 002-2v-6a2 2 0 00-2-2H6a2 2 0 00-2 2v6a2 2 0 002 2zm10-10V7a4 4 0 00-8 0v4h8z"></path>
								</svg>
							</div>
							<h4 class="text-lg font-semibold text-white mb-2">Secure & Compliant</h4>
							<p class="text-emerald-100 text-sm">GDPR & Kenya Data Protection ready</p>
						</div>
						<div class="text-center p-6 bg-white/5 backdrop-blur-sm rounded-xl border border-white/10">
							<div class="w-12 h-12 bg-white/10 rounded-full flex items-center justify-center mx-auto mb-4">
								<svg class="w-6 h-6 text-white" fill="none" stroke="currentColor" viewBox="0 0 24 24">
									<path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M9 12l2 2 4-4m6 2a9 9 0 11-18 0 9 9 0 0118 0z"></path>
								</svg>
							</div>
							<h4 class="text-lg font-semibold text-white mb-2">Proven Results</h4>
							<p class="text-emerald-100 text-sm">Award-winning designs & 300%+ ROI</p>
						</div>
						<div class="text-center p-6 bg-white/5 backdrop-blur-sm rounded-xl border border-white/10">
							<div class="w-12 h-12 bg-white/10 rounded-full flex items-center justify-center mx-auto mb-4">
								<svg class="w-6 h-6 text-white" fill="none" stroke="currentColor" viewBox="0 0 24 24">
									<path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M18.364 5.636l-3.536 3.536m0 5.656l3.536 3.536M9.172 9.172L5.636 5.636m3.536 9.192L5.636 18.364M12 2.25a9.75 9.75 0 109.75 9.75A9.75 9.75 0 0012 2.25z"></path>
								</svg>
							</div>
							<h4 class="text-lg font-semibold text-white mb-2">Full Support</h4>
							<p class="text-emerald-100 text-sm">12-month warranty & ongoing maintenance</p>
						</div>
					</div>
				</div>
			</div>
		</section>

		</div>
	</main>

	<!-- Footer -->
	<footer class="bg-slate-900 text-white py-8 mt-16">
		<div class="max-w-4xl mx-auto px-6 text-center">
			<p class="text-slate-400">© 2024 Leon Kalema. Professional web development for sustainable brands.</p>
		</div>
	</footer>
</div>

<style>
	.animate-fade-in {
		animation: fadeIn 0.8s ease-out forwards;
	}
	
	.animate-fade-in-delay {
		animation: fadeIn 0.8s ease-out 0.2s forwards;
	}
	
	.animate-fade-in-delay-2 {
		animation: fadeIn 0.8s ease-out 0.4s forwards;
	}
	
	.animate-fade-in-delay-3 {
		animation: fadeIn 0.8s ease-out 0.6s forwards;
	}
	
	.animate-fade-in-delay-4 {
		animation: fadeIn 0.8s ease-out 0.8s forwards;
	}
	
	.animate-fade-in-delay-5 {
		animation: fadeIn 0.8s ease-out 1.0s forwards;
	}
	
	.animate-fade-in-delay-6 {
		animation: fadeIn 0.8s ease-out 1.2s forwards;
	}

	@keyframes fadeIn {
		from {
			opacity: 0;
			transform: translateY(20px);
		}
		to {
			opacity: 1;
			transform: translateY(0);
		}
	}
</style>
