<script lang="ts">
  import { onMount } from 'svelte';

  // Images - using Unsplash for realistic placeholders
  const images = {
    hero: "https://images.unsplash.com/photo-1531746020798-e6953c6e8e04?q=80&w=2550&auto=format&fit=crop", // Close up face
    dashboard: "https://plus.unsplash.com/premium_photo-1681487814165-018814e29155?q=80&w=2070&auto=format&fit=crop", // Tablet/Dashboard
    bloodDraw: "https://images.unsplash.com/photo-1579154204601-01588f351e67?q=80&w=2070&auto=format&fit=crop", // Blood draw
    app: "https://images.unsplash.com/photo-1512428559087-560fa0db7f0c?q=80&w=2070&auto=format&fit=crop", // Phone app
    supplements: "https://images.unsplash.com/photo-1584308666744-24d5c474f2ae?q=80&w=2030&auto=format&fit=crop", // Supplements
    runner: "https://images.unsplash.com/photo-1452626038306-9aae5e071dd3?q=80&w=2074&auto=format&fit=crop", // Runner
    card: "https://images.unsplash.com/photo-1628191011993-43508d53bb52?q=80&w=1000&auto=format&fit=crop" // Abstract card
  };

  const doctors = [
    { name: "Dr Anant Vinjamoori", title: "Superpower Chief Longevity Officer, Harvard MD & MBA", img: "https://images.unsplash.com/photo-1612349317150-e413f6a5b16d?q=80&w=500&auto=format&fit=crop" },
    { name: "Dr Leigh Erin Connealy", title: "Clinician & Founder of The Centre for New Medicine", img: "https://images.unsplash.com/photo-1559839734-2b71ea197ec2?q=80&w=500&auto=format&fit=crop" },
    { name: "Dr Abe Malkin", title: "Founder & Medical Director of Concierge MD", img: "https://images.unsplash.com/photo-1622253692010-333f2da6031d?q=80&w=500&auto=format&fit=crop" },
    { name: "Dr Robert Lufkin", title: "UCLA Medical Professor, NYT Bestselling Author", img: "https://images.unsplash.com/photo-1537368910025-700350fe46c7?q=80&w=500&auto=format&fit=crop" }
  ];

  const faqs = [
    { q: "What should I expect during a blood draw?", a: "A quick and professional experience at one of our 2,000+ partner locations." },
    { q: "How do I prepare for a blood draw?", a: "Fast for 12 hours prior to your appointment and drink plenty of water." },
    { q: "What should I do after my blood draw?", a: "Resume your normal diet and activities immediately." },
    { q: "How do I book a blood draw with Superpower?", a: "You can book directly through your dashboard after signing up." },
    { q: "Where can I take my blood test?", a: "We have over 2,000 locations nationwide." },
    { q: "Does Superpower replace my primary care provider?", a: "No, we work alongside your primary care provider to give you deeper insights." },
    { q: "How fast are blood test results and how do I read them?", a: "Results are typically available within 5 business days." },
    { q: "Does Superpower accept health insurance?", a: "We accept HSA/FSA payments, but do not bill insurance directly." },
    { q: "What if I want more than 1 blood test per year?", a: "You can purchase additional add-on tests at any time." }
  ];

  const biomarkers = [
    { category: "Heart & Vascular Health", icon: "❤️" },
    { category: "Kidney Health", icon: "🧬" },
    { category: "Metabolic Health", icon: "⚡" },
    { category: "Inflammation", icon: "🔥" },
    { category: "Energy", icon: "🔋" },
    { category: "Body Composition", icon: "💪" },
    { category: "Liver Health", icon: "🧪" },
    { category: "Sex Hormones", icon: "⚧" },
    { category: "Nutrients", icon: "🥗" },
    { category: "Thyroid Health", icon: "🦋" },
    { category: "Immune System", icon: "🛡️" },
    { category: "DNA Health", icon: "🧬" }
  ];

  const biomarkerList = [
    "ADMA", "Atherogenic Coefficient", "Cholesterol, Total", "Cystatin C (with eGFR)", "HDL P (Advanced panel)", "LDL Cholesterol", "LDL P (Advanced panel)", "LDL-C / ApoB", "Large HDL P (Advanced panel)", "Lipoprotein (a) (Advanced panel)",
    "Apolipoprotein B (ApoB)", "Atherogenic Index of Plasma (AIP)", "Cholesterol/HDL Ratio", "HDL Cholesterol", "HDL Size (Advanced panel)", "LDL Cholesterol / Total Cholesterol (Mass Ratio)", "LDL Size (Advanced panel)", "LDL/HDL Ratio", "Large VLDL P (Advanced panel)", "Lipoprotein fractionation"
  ];
</script>

<main class="w-full overflow-hidden">
  <!-- Hero Section -->
  <section class="relative h-screen min-h-[700px] w-full flex items-center justify-center text-center text-white">
    <div class="absolute inset-0 z-0">
      <img src={images.hero} alt="Hero" class="w-full h-full object-cover object-top brightness-[0.6]" />
      <div class="absolute inset-0 bg-black/20"></div>
    </div>
    
    <div class="relative z-10 max-w-4xl mx-auto px-6 pt-20">
      <h1 class="text-5xl md:text-7xl font-bold tracking-tight mb-6 leading-tight">
        Unlock your new<br />health intelligence
      </h1>
      <p class="text-lg md:text-xl text-white/90 mb-10 max-w-2xl mx-auto leading-relaxed">
        100+ lab tests. Every year. Detect early signs of 1,000+ conditions. All for only $17/month
      </p>
      <div class="flex flex-col items-center gap-4">
        <a href="/join" class="bg-brand-orange hover:bg-brand-orange-hover text-white text-base font-semibold px-8 py-4 rounded-full transition-colors inline-flex items-center gap-2">
          Join Today
          <svg xmlns="http://www.w3.org/2000/svg" width="18" height="18" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"><path d="m9 18 6-6-6-6"/></svg>
        </a>
        <div class="flex items-center gap-2 text-sm text-white/80">
          <svg xmlns="http://www.w3.org/2000/svg" width="16" height="16" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round" class="text-white"><polyline points="20 6 9 17 4 12"></polyline></svg>
          HSA/FSA eligible
        </div>
      </div>
    </div>
  </section>

  <!-- Benefits Bar -->
  <section class="py-12 bg-white border-b border-gray-100">
    <div class="max-w-[1400px] mx-auto px-6 grid grid-cols-1 md:grid-cols-3 gap-8 text-center">
      <div class="flex flex-col items-center gap-2">
        <div class="flex items-center gap-2 font-semibold text-gray-900">
            <svg xmlns="http://www.w3.org/2000/svg" width="20" height="20" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"><circle cx="12" cy="12" r="10"/><polyline points="12 6 12 12 16 14"/></svg>
            No wait times
        </div>
        <p class="text-sm text-gray-500">less than 15 minute lab visit</p>
      </div>
      <div class="flex flex-col items-center gap-2">
        <div class="flex items-center gap-2 font-semibold text-gray-900">
            <svg xmlns="http://www.w3.org/2000/svg" width="20" height="20" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"><path d="M13 2L3 14h9l-1 8 10-12h-9l1-8z"/></svg>
            Fast results
        </div>
        <p class="text-sm text-gray-500">Get your result in 5 business days</p>
      </div>
      <div class="flex flex-col items-center gap-2">
        <div class="flex items-center gap-2 font-semibold text-gray-900">
            <svg xmlns="http://www.w3.org/2000/svg" width="20" height="20" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"><path d="M21 10c0 7-9 13-9 13s-9-6-9-13a9 9 0 0 1 18 0z"/><circle cx="12" cy="10" r="3"/></svg>
            Simple and convenient
        </div>
        <p class="text-sm text-gray-500">Book your test at over 2,000+ locations</p>
      </div>
    </div>
  </section>

  <!-- Dashboard Preview -->
  <section class="py-24 bg-gray-50 overflow-hidden">
    <div class="max-w-[1400px] mx-auto px-6 text-center">
      <h2 class="text-4xl md:text-5xl font-bold tracking-tight mb-6">It starts with 100+ labs</h2>
      <p class="text-lg text-gray-600 max-w-3xl mx-auto mb-8">
        From heart health to hormone balance our comprehensive test panels detect early signs of over 1,000 conditions
      </p>
      <a href="#" class="inline-flex items-center gap-1 text-sm font-medium text-gray-900 hover:text-brand-orange transition-colors mb-16">
        Explore all biomarkers
        <svg xmlns="http://www.w3.org/2000/svg" width="16" height="16" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"><path d="m9 18 6-6-6-6"/></svg>
      </a>
      
      <div class="relative mx-auto max-w-5xl shadow-2xl rounded-3xl overflow-hidden border border-gray-200 bg-white">
        <!-- Mockup of dashboard -->
        <img src={images.dashboard} alt="Dashboard Interface" class="w-full h-auto" />
      </div>
    </div>
  </section>

  <!-- Testimonials -->
  <section class="py-24 bg-white">
    <div class="max-w-4xl mx-auto px-6 text-center">
      <blockquote class="text-2xl md:text-4xl font-medium leading-tight mb-8">
        “Superpower gave me what no doctor, supplement, or app ever could: clarity. If you're tired of vague advice and want real insight into your body, it's worth it.”
      </blockquote>
      <a href="#" class="inline-flex items-center gap-1 text-sm font-medium text-gray-900 hover:text-brand-orange transition-colors mb-20">
        Read reviews
        <svg xmlns="http://www.w3.org/2000/svg" width="16" height="16" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"><path d="m9 18 6-6-6-6"/></svg>
      </a>

      <div class="grid grid-cols-1 md:grid-cols-3 gap-12 text-left border-t border-gray-100 pt-12">
        <div>
          <div class="text-5xl font-bold mb-2">63<span class="text-2xl align-top">%</span></div>
          <p class="text-sm text-gray-600">of members find<br/>early risk factors for diabetes</p>
        </div>
        <div>
          <div class="text-5xl font-bold mb-2">44<span class="text-2xl align-top">%</span></div>
          <p class="text-sm text-gray-600">of members find<br/>elevated heart disease risk</p>
        </div>
        <div>
          <div class="text-5xl font-bold mb-2">70<span class="text-2xl align-top">%</span></div>
          <p class="text-sm text-gray-600">of members slow<br/>their speed of ageing</p>
        </div>
      </div>
    </div>
  </section>

  <!-- How it works -->
  <section class="py-24 bg-white" id="how-it-works">
    <div class="max-w-[1400px] mx-auto px-6">
      <h2 class="text-4xl md:text-5xl font-bold tracking-tight mb-16">How it works</h2>
      
      <div class="grid grid-cols-1 md:grid-cols-3 gap-8">
        <!-- Step 1 -->
        <div class="group">
          <div class="relative aspect-[4/3] rounded-2xl overflow-hidden mb-8 bg-gray-100">
             <img src={images.bloodDraw} alt="Blood draw" class="w-full h-full object-cover transition-transform duration-500 group-hover:scale-105" />
             <div class="absolute top-4 left-4 w-8 h-8 bg-brand-orange text-white flex items-center justify-center rounded text-sm font-bold">1</div>
          </div>
          <h3 class="text-2xl font-bold mb-3">Test your whole body</h3>
          <p class="text-gray-600 leading-relaxed">
            Get a comprehensive blood draw at one of our 2,000+ partner labs or from the comfort of your own home.
          </p>
        </div>

        <!-- Step 2 -->
        <div class="group">
          <div class="relative aspect-[4/3] rounded-2xl overflow-hidden mb-8 bg-gray-100">
             <img src={images.app} alt="App interface" class="w-full h-full object-cover transition-transform duration-500 group-hover:scale-105" />
             <div class="absolute top-4 left-4 w-8 h-8 bg-brand-orange text-white flex items-center justify-center rounded text-sm font-bold">2</div>
          </div>
          <h3 class="text-2xl font-bold mb-3">An actionable plan</h3>
          <p class="text-gray-600 leading-relaxed">
            Easy to understand results and a clear health plan with tailored recommendations on diet, lifestyle changes & supplements.
          </p>
        </div>

        <!-- Step 3 -->
        <div class="group">
          <div class="relative aspect-[4/3] rounded-2xl overflow-hidden mb-8 bg-gray-100">
             <img src={images.supplements} alt="Supplements" class="w-full h-full object-cover transition-transform duration-500 group-hover:scale-105" />
             <div class="absolute top-4 left-4 w-8 h-8 bg-brand-orange text-white flex items-center justify-center rounded text-sm font-bold">3</div>
          </div>
          <h3 class="text-2xl font-bold mb-3">A connected ecosystem</h3>
          <p class="text-gray-600 leading-relaxed">
            You can book additional diagnostics, buy curated supplements with members-only discounts in your Superpower dashboard.
          </p>
        </div>
      </div>
    </div>
  </section>

  <!-- Social Proof -->
  <section class="py-24 bg-gray-50 overflow-hidden">
    <div class="max-w-[1400px] mx-auto px-6">
        <div class="flex justify-between items-end mb-12">
            <h2 class="text-3xl md:text-4xl font-bold tracking-tight max-w-xl">Superpower is changing thousands of lives</h2>
            <a href="#" class="text-sm font-medium text-gray-600 hover:text-brand-orange hidden md:block">See more reviews</a>
        </div>
        
        <div class="flex gap-6 overflow-x-auto pb-8 snap-x">
            <!-- Video Cards placeholders -->
            {#each [1, 2, 3, 4] as i}
            <div class="min-w-[280px] h-[500px] bg-black rounded-2xl relative overflow-hidden flex-shrink-0 snap-center">
                <img src={`https://images.unsplash.com/photo-${i === 1 ? '1534528741775-53994a69daeb' : i === 2 ? '1517841905240-472988babdf9' : i === 3 ? '1539571696357-5a69c17a67c6' : '1507003211169-0a1dd7228f2d'}?q=80&w=600&auto=format&fit=crop`} alt="Review" class="w-full h-full object-cover opacity-80" />
                <div class="absolute bottom-0 left-0 right-0 p-4 bg-gradient-to-t from-black/80 to-transparent text-white">
                    <p class="font-medium text-sm">@user{i}</p>
                    <p class="text-xs opacity-80 mt-1">"Changed my life completely..."</p>
                </div>
                <div class="absolute top-4 left-4 w-8 h-8 rounded-full bg-white/20 backdrop-blur flex items-center justify-center">
                    <svg xmlns="http://www.w3.org/2000/svg" width="16" height="16" viewBox="0 0 24 24" fill="white" stroke="none"><polygon points="5 3 19 12 5 21 5 3"/></svg>
                </div>
            </div>
            {/each}
        </div>
        
        <div class="flex justify-center gap-4 mt-4">
            <button class="w-10 h-10 rounded-full border border-gray-300 flex items-center justify-center hover:bg-gray-100">
                <svg xmlns="http://www.w3.org/2000/svg" width="20" height="20" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"><path d="m15 18-6-6 6-6"/></svg>
            </button>
            <button class="w-10 h-10 rounded-full border border-gray-300 flex items-center justify-center hover:bg-gray-100">
                <svg xmlns="http://www.w3.org/2000/svg" width="20" height="20" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"><path d="m9 18 6-6-6-6"/></svg>
            </button>
        </div>
    </div>
  </section>

  <!-- What's included -->
  <section class="py-24 bg-white">
    <div class="max-w-[1400px] mx-auto px-6">
      <div class="flex flex-col lg:flex-row gap-16">
        <div class="lg:w-1/3 lg:sticky lg:top-32 h-fit">
          <h2 class="text-4xl font-bold tracking-tight mb-6">What's included in your membership</h2>
          <p class="text-gray-600 mb-8 leading-relaxed">
            Superpower is more than a blood test. Access an ecosystem of diagnostics and doctor-trusted solutions personalized to you.
          </p>
          <a href="/join" class="bg-brand-orange hover:bg-brand-orange-hover text-white text-sm font-semibold px-6 py-3 rounded-full transition-colors inline-flex items-center gap-2">
            Join Today
            <svg xmlns="http://www.w3.org/2000/svg" width="16" height="16" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"><path d="m9 18 6-6-6-6"/></svg>
          </a>
        </div>

        <div class="lg:w-2/3 grid grid-cols-1 md:grid-cols-2 gap-6">
            <!-- Card 1 -->
            <div class="bg-gray-50 rounded-3xl p-8 flex flex-col h-[400px]">
                <div class="flex-1 bg-white rounded-xl mb-6 shadow-sm overflow-hidden relative">
                    <img src={images.dashboard} alt="Data" class="w-full h-full object-cover" />
                </div>
                <h3 class="text-xl font-bold mb-2">All your data in one place</h3>
                <p class="text-sm text-gray-600">100+ labs, your biological age & health report.</p>
            </div>
            
            <!-- Card 2 -->
            <div class="bg-gray-50 rounded-3xl p-8 flex flex-col h-[400px]">
                <div class="flex-1 bg-white rounded-xl mb-6 shadow-sm overflow-hidden relative p-4 flex items-center justify-center">
                    <div class="w-full h-32 bg-green-50 rounded-lg border border-green-100 relative">
                        <!-- Abstract chart -->
                        <svg class="w-full h-full text-green-500" viewBox="0 0 100 50" preserveAspectRatio="none">
                            <path d="M0 50 L20 40 L40 45 L60 20 L80 30 L100 10" fill="none" stroke="currentColor" stroke-width="2"/>
                            <circle cx="20" cy="40" r="2" fill="currentColor"/>
                            <circle cx="60" cy="20" r="2" fill="currentColor"/>
                            <circle cx="100" cy="10" r="2" fill="currentColor"/>
                        </svg>
                    </div>
                </div>
                <h3 class="text-xl font-bold mb-2">Upload past lab data</h3>
                <p class="text-sm text-gray-600">Visualize past Quest or Labcorp results.</p>
            </div>

            <!-- Card 3 -->
            <div class="bg-gray-50 rounded-3xl p-8 flex flex-col h-[400px]">
                <div class="flex-1 bg-white rounded-xl mb-6 shadow-sm overflow-hidden relative">
                     <img src={images.app} alt="Plan" class="w-full h-full object-cover" />
                </div>
                <h3 class="text-xl font-bold mb-2">Your personalized health plan</h3>
                <p class="text-sm text-gray-600">Lifestyle, diet, supplement & Rx recommendations.</p>
            </div>

            <!-- Card 4 -->
            <div class="bg-gray-50 rounded-3xl p-8 flex flex-col h-[400px]">
                <div class="flex-1 bg-white rounded-xl mb-6 shadow-sm overflow-hidden relative flex items-center justify-center bg-gray-100">
                     <div class="text-center p-4">
                        <div class="w-12 h-12 bg-gray-300 rounded-full mx-auto mb-2"></div>
                        <div class="bg-white p-2 rounded-lg shadow-sm text-xs text-left max-w-[150px]">What supplements would you recommend for me?</div>
                     </div>
                </div>
                <h3 class="text-xl font-bold mb-2">Unlimited concierge messaging</h3>
                <p class="text-sm text-gray-600">Ask questions and get answers from our care team.</p>
            </div>
            
            <!-- Card 5 -->
            <div class="bg-gray-50 rounded-3xl p-8 flex flex-col h-[300px]">
                <div class="flex-1 bg-white rounded-xl mb-6 shadow-sm overflow-hidden relative">
                     <img src="https://images.unsplash.com/photo-1584017911766-d451b3d0e843?q=80&w=2069&auto=format&fit=crop" alt="Kits" class="w-full h-full object-cover" />
                </div>
                <h3 class="text-lg font-bold mb-1">Add-on testing anytime</h3>
                <p class="text-xs text-gray-600">Advanced gut microbiome, toxins & cancer screens.</p>
            </div>

            <!-- Card 6 -->
            <div class="bg-gray-50 rounded-3xl p-8 flex flex-col h-[300px]">
                <div class="flex-1 bg-white rounded-xl mb-6 shadow-sm overflow-hidden relative">
                     <img src={images.supplements} alt="Clinic" class="w-full h-full object-cover" />
                </div>
                <h3 class="text-lg font-bold mb-1">Access to Superpower Clinic</h3>
                <p class="text-xs text-gray-600">Curated solutions available after medical evaluation.</p>
            </div>
        </div>
      </div>
    </div>
  </section>

  <!-- Medical Professionals -->
  <section class="py-24 bg-white">
    <div class="max-w-[1400px] mx-auto px-6">
      <div class="flex flex-col md:flex-row justify-between items-start md:items-end mb-16 gap-8">
        <div>
            <h2 class="text-3xl md:text-4xl font-bold tracking-tight mb-4">Developed by world-class medical<br/>professionals</h2>
            <p class="text-gray-600">Supported by the world's top longevity clinicians and MDs.</p>
        </div>
        <div class="flex gap-8 opacity-60 grayscale">
            <!-- Logos -->
            <span class="text-xl font-serif font-bold">Stanford</span>
            <span class="text-xl font-serif font-bold">HARVARD</span>
            <span class="text-xl font-serif font-bold">Ucla</span>
        </div>
      </div>

      <div class="grid grid-cols-1 md:grid-cols-4 gap-6">
        {#each doctors as doctor}
        <div class="group">
            <div class="aspect-square rounded-2xl overflow-hidden mb-4 bg-gray-100">
                <img src={doctor.img} alt={doctor.name} class="w-full h-full object-cover transition-transform duration-500 group-hover:scale-105" />
            </div>
            <h3 class="font-bold text-lg mb-1">{doctor.name}</h3>
            <p class="text-xs text-gray-500 leading-relaxed">{doctor.title}</p>
        </div>
        {/each}
      </div>
    </div>
  </section>

  <!-- Pricing -->
  <section class="py-24 bg-white">
    <div class="max-w-[1200px] mx-auto px-6">
        <div class="grid grid-cols-1 md:grid-cols-2 gap-16 items-center">
            <div class="relative">
                <div class="aspect-[1.58/1] rounded-3xl overflow-hidden shadow-2xl relative bg-gradient-to-br from-orange-400 to-red-500 p-8 text-white flex flex-col justify-between">
                    <!-- Card Content -->
                    <div class="flex justify-between items-start">
                        <span class="font-bold text-2xl tracking-tight">superpower<br/>membership</span>
                        <div class="w-12 h-8 bg-white/20 rounded-md"></div>
                    </div>
                    <div>
                        <div class="text-4xl font-bold mb-1">$17 <span class="text-lg font-normal">/month</span></div>
                        <div class="text-xs opacity-80">Billed annually at $199</div>
                    </div>
                </div>
            </div>

            <div>
                <div class="text-sm text-gray-500 mb-2">What could cost you $15,000 is $199</div>
                <h2 class="text-5xl font-bold tracking-tight mb-8">Superpower<br/>Membership</h2>
                <p class="text-gray-600 mb-8">Your membership includes one comprehensive blood draw each year, covering 100+ biomarkers in a single collection</p>
                
                <ul class="space-y-4 mb-10">
                    <li class="flex gap-3 items-start">
                        <svg class="w-5 h-5 text-brand-orange mt-0.5 flex-shrink-0" fill="none" stroke="currentColor" viewBox="0 0 24 24"><path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M5 13l4 4L19 7"></path></svg>
                        <span class="text-sm text-gray-700">One appointment, one draw for your annual panel.</span>
                    </li>
                    <li class="flex gap-3 items-start">
                        <svg class="w-5 h-5 text-brand-orange mt-0.5 flex-shrink-0" fill="none" stroke="currentColor" viewBox="0 0 24 24"><path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M5 13l4 4L19 7"></path></svg>
                        <span class="text-sm text-gray-700">100+ labs tested per year</span>
                    </li>
                    <li class="flex gap-3 items-start">
                        <svg class="w-5 h-5 text-brand-orange mt-0.5 flex-shrink-0" fill="none" stroke="currentColor" viewBox="0 0 24 24"><path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M5 13l4 4L19 7"></path></svg>
                        <span class="text-sm text-gray-700">A personalized plan that evolves with you</span>
                    </li>
                    <li class="flex gap-3 items-start">
                        <svg class="w-5 h-5 text-brand-orange mt-0.5 flex-shrink-0" fill="none" stroke="currentColor" viewBox="0 0 24 24"><path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M5 13l4 4L19 7"></path></svg>
                        <span class="text-sm text-gray-700">Get your biological age and track your health over a lifetime</span>
                    </li>
                </ul>

                <div class="flex items-baseline gap-2 mb-2">
                    <span class="text-5xl font-bold">$17</span>
                    <span class="text-gray-500">/ month - billed annually</span>
                </div>
                <p class="text-xs text-gray-400 mb-8">Pricing for members in NY & NJ is $499 <span class="inline-block w-3 h-3 rounded-full bg-gray-200 text-center leading-3 text-[8px]">?</span></p>

                <div class="flex flex-col gap-4">
                    <a href="/join" class="bg-brand-orange hover:bg-brand-orange-hover text-white text-center font-semibold py-4 rounded-full transition-colors w-full">
                        Start testing >
                    </a>
                    <div class="flex justify-between items-center text-[10px] text-gray-400 uppercase tracking-wide">
                        <span>Flexible payment options</span>
                        <div class="flex gap-2">
                            <!-- Payment Icons -->
                             <div class="w-8 h-5 bg-gray-100 rounded"></div>
                             <div class="w-8 h-5 bg-gray-100 rounded"></div>
                             <div class="w-8 h-5 bg-gray-100 rounded"></div>
                        </div>
                    </div>
                    <div class="flex justify-center gap-6 text-[10px] text-gray-400">
                        <span class="flex items-center gap-1"><svg class="w-3 h-3" fill="none" stroke="currentColor" viewBox="0 0 24 24"><path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M5 13l4 4L19 7"></path></svg> Cancel anytime</span>
                        <span class="flex items-center gap-1"><svg class="w-3 h-3" fill="none" stroke="currentColor" viewBox="0 0 24 24"><path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M5 13l4 4L19 7"></path></svg> HSA/FSA eligible</span>
                        <span class="flex items-center gap-1"><svg class="w-3 h-3" fill="none" stroke="currentColor" viewBox="0 0 24 24"><path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M5 13l4 4L19 7"></path></svg> Results in a week</span>
                    </div>
                </div>
            </div>
        </div>
    </div>
  </section>

  <!-- FAQ -->
  <section class="py-24 bg-gray-50" id="faqs">
    <div class="max-w-[1200px] mx-auto px-6">
        <div class="flex justify-between items-center mb-12">
            <h2 class="text-3xl md:text-4xl font-bold tracking-tight">Frequently Asked Questions</h2>
            <button class="px-4 py-2 bg-white border border-gray-200 rounded-full text-sm font-medium hover:bg-gray-50">Read more</button>
        </div>

        <div class="flex flex-col md:flex-row gap-12">
            <div class="w-full md:w-1/4 space-y-4">
                <button class="text-left font-medium text-gray-900 block w-full">How it works</button>
                <button class="text-left font-medium text-gray-400 block w-full hover:text-gray-600">Our testing</button>
            </div>
            <div class="w-full md:w-3/4 space-y-4">
                {#each faqs as faq}
                <div class="border-b border-gray-200 pb-4">
                    <details class="group">
                        <summary class="flex justify-between items-center font-medium cursor-pointer list-none text-gray-800">
                            <span>{faq.q}</span>
                            <span class="transition group-open:rotate-180">
                                <svg fill="none" height="24" shape-rendering="geometricPrecision" stroke="currentColor" stroke-linecap="round" stroke-linejoin="round" stroke-width="1.5" viewBox="0 0 24 24" width="24"><path d="M6 9l6 6 6-6"></path></svg>
                            </span>
                        </summary>
                        <p class="text-gray-600 mt-3 group-open:animate-fadeIn text-sm leading-relaxed">
                            {faq.a}
                        </p>
                    </details>
                </div>
                {/each}
            </div>
        </div>
    </div>
  </section>

  <!-- Biomarkers -->
  <section class="py-24 bg-white" id="what-we-test">
    <div class="max-w-[1400px] mx-auto px-6">
        <h2 class="text-3xl md:text-4xl font-bold tracking-tight mb-2">See everything we test</h2>
        <p class="text-gray-600 mb-12">The following 100+ biomarkers are included with your annual Superpower membership.</p>

        <div class="grid grid-cols-1 lg:grid-cols-4 gap-12">
            <div class="lg:col-span-1 space-y-2">
                {#each biomarkers as bio}
                <div class="flex items-center gap-3 p-2 rounded hover:bg-gray-50 cursor-pointer transition-colors text-sm font-medium text-gray-700">
                    <span class="text-lg">{bio.icon}</span>
                    {bio.category}
                </div>
                {/each}
            </div>
            <div class="lg:col-span-3">
                <div class="grid grid-cols-1 md:grid-cols-2 lg:grid-cols-3 gap-x-8 gap-y-2">
                    {#each biomarkerList as item}
                    <div class="flex items-center justify-between py-2 border-b border-gray-50 text-xs font-medium text-gray-800">
                        <span>{item.replace(/ \(.*\)/, '')}</span>
                        {#if item.includes('Advanced panel')}
                        <span class="bg-gray-100 text-gray-500 text-[10px] px-1.5 py-0.5 rounded">Advanced panel</span>
                        {/if}
                    </div>
                    {/each}
                    <!-- Repeating list to fill space as in screenshot -->
                    {#each biomarkerList as item}
                    <div class="flex items-center justify-between py-2 border-b border-gray-50 text-xs font-medium text-gray-800">
                        <span>{item.replace(/ \(.*\)/, '')}</span>
                        {#if item.includes('Advanced panel')}
                        <span class="bg-gray-100 text-gray-500 text-[10px] px-1.5 py-0.5 rounded">Advanced panel</span>
                        {/if}
                    </div>
                    {/each}
                </div>
            </div>
        </div>
    </div>
  </section>

  <!-- Bottom CTA -->
  <section class="relative h-[600px] flex items-center justify-center text-center overflow-hidden">
    <div class="absolute inset-0 z-0">
        <img src={images.runner} alt="Runner" class="w-full h-full object-cover object-center brightness-[0.4]" />
    </div>
    <div class="relative z-10 max-w-4xl px-6">
        <h2 class="text-4xl md:text-6xl font-bold tracking-tight text-white mb-8 leading-tight">
            Health is your greatest<br/>superpower. It's time<br/>to unlock it.
        </h2>
        <a href="/join" class="bg-brand-orange hover:bg-brand-orange-hover text-white text-base font-semibold px-8 py-4 rounded-full transition-colors inline-flex items-center gap-2">
            Start testing >
        </a>
    </div>
  </section>

</main>

<style>
  /* Custom scrollbar for horizontal scroll areas */
  .snap-x::-webkit-scrollbar {
    display: none;
  }
  .snap-x {
    -ms-overflow-style: none;
    scrollbar-width: none;
  }
</style>

