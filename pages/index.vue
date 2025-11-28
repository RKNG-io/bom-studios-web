<template>
  <div>
    <!-- Language Switcher -->
    <div class="language-switcher">
      <button
        :class="['lang-btn', { active: currentLanguage === 'en' }]"
        @click="currentLanguage = 'en'"
      >
        English
      </button>
      <button
        :class="['lang-btn', { active: currentLanguage === 'nl' }]"
        @click="currentLanguage = 'nl'"
      >
        Nederlands
      </button>
    </div>

    <!-- Hero Section -->
    <section class="hero" id="hero">
      <div class="warp-pattern"></div>
      <div class="container">
        <div class="hero-content">
          <div class="tagline">{{ copy.hero.tagline }}</div>
          <h1>{{ copy.hero.headline }}</h1>
          <p class="hero-subhead">{{ copy.hero.subhead }}</p>
          <div class="hero-cta">
            <button class="btn btn-primary">{{ copy.hero.cta1 }}</button>
            <button class="btn btn-secondary">{{ copy.hero.cta2 }}</button>
          </div>
          <p class="microline">{{ copy.hero.microline }}</p>
        </div>
      </div>
    </section>

    <!-- Why Video Section -->
    <section id="why-video">
      <div class="warp-pattern"></div>
      <div class="container">
        <div class="section-header text-center">
          <h2>{{ copy.whyVideo.headline }}</h2>
        </div>
        <div class="stats-grid">
          <div class="stat-card">
            <div class="stat-number">3×</div>
            <p>{{ copy.whyVideo.stat1 }}</p>
          </div>
          <div class="stat-card">
            <div class="stat-number">95%</div>
            <p>{{ copy.whyVideo.stat2 }}</p>
          </div>
          <div class="stat-card">
            <div class="stat-number">86%</div>
            <p>{{ copy.whyVideo.stat3 }}</p>
          </div>
          <div class="stat-card">
            <div class="stat-number">91%</div>
            <p>{{ copy.whyVideo.stat4 }}</p>
          </div>
        </div>
        <div class="bottom-line">
          <p>{{ copy.whyVideo.bottomLine }}</p>
        </div>
      </div>
    </section>

    <!-- Quality Section -->
    <section id="quality">
      <div class="warp-pattern"></div>
      <div class="container">
        <div class="section-header">
          <h2>{{ copy.quality.headline }}</h2>
          <p class="quality-description">{{ copy.quality.description }}</p>
        </div>

        <div class="guarantees-grid">
          <div class="guarantee-card" v-for="(guarantee, index) in copy.quality.guarantees" :key="index">
            <div class="guarantee-icon">✓</div>
            <h3>{{ guarantee }}</h3>
          </div>
        </div>

        <p class="quality-microline">{{ copy.quality.microline }}</p>
      </div>
    </section>

    <!-- How It Works Section -->
    <section id="how-it-works">
      <div class="warp-pattern"></div>
      <div class="container">
        <div class="section-header text-center">
          <h2>{{ copy.howItWorks.headline }}</h2>
          <p>{{ copy.howItWorks.subhead }}</p>
        </div>

        <div class="pipeline-steps">
          <div class="pipeline-step" v-for="(step, index) in copy.howItWorks.steps" :key="index">
            <div class="step-number">{{ index + 1 }}</div>
            <h3>{{ step.title }}</h3>
            <p>{{ step.description }}</p>
          </div>
        </div>
      </div>
    </section>

    <!-- Video Styles Section -->
    <section id="video-styles">
      <div class="warp-pattern"></div>
      <div class="container">
        <div class="section-header text-center">
          <h2>{{ copy.styles.headline }}</h2>
        </div>

        <div class="styles-grid">
          <div class="style-card card" v-for="(style, index) in copy.styles.items" :key="index">
            <h3>{{ style.title }}</h3>
            <p>{{ style.description }}</p>
          </div>
        </div>
      </div>
    </section>

    <!-- Durations Section -->
    <section id="durations">
      <div class="warp-pattern"></div>
      <div class="container">
        <div class="section-header text-center">
          <h2>{{ copy.durations.headline }}</h2>
        </div>

        <div class="durations-grid">
          <div class="duration-card card" v-for="(duration, index) in copy.durations.items" :key="index">
            <h3>{{ duration.title }}</h3>
            <p>{{ duration.description }}</p>
          </div>
        </div>
      </div>
    </section>

    <!-- Pricing Section -->
    <section id="pricing">
      <div class="warp-pattern"></div>
      <div class="container">
        <div class="section-header text-center">
          <h2>{{ copy.pricing.headline }}</h2>
        </div>

        <div class="pricing-grid">
          <div
            class="pricing-card card"
            :class="{ featured: index === 1 }"
            v-for="(plan, index) in copy.pricing.plans"
            :key="index"
          >
            <div v-if="index === 1" class="featured-badge">{{ copy.pricing.mostPopular }}</div>
            <h3>{{ plan.title }}</h3>
            <div class="price">{{ plan.price }}</div>
            <p class="price-label">{{ plan.period }}</p>
            <p class="price-description">{{ plan.description }}</p>
            <button class="btn btn-primary btn-full">{{ copy.pricing.cta }}</button>
          </div>
        </div>
      </div>
    </section>

    <!-- FAQ Section -->
    <section id="faq">
      <div class="warp-pattern"></div>
      <div class="container">
        <div class="section-header text-center">
          <h2>{{ copy.faq.headline }}</h2>
        </div>

        <div class="faq-grid">
          <div class="faq-item" v-for="(item, index) in copy.faq.items" :key="index">
            <h3>{{ item.question }}</h3>
            <p>{{ item.answer }}</p>
          </div>
        </div>
      </div>
    </section>

    <!-- Final CTA Section -->
    <section id="final-cta" class="final-cta-section">
      <div class="warp-pattern"></div>
      <div class="container">
        <div class="final-cta-content">
          <h2>{{ copy.finalCta.headline }}</h2>
          <p>{{ copy.finalCta.subhead }}</p>
          <button class="btn btn-primary btn-large">{{ copy.finalCta.cta }}</button>
        </div>
      </div>
    </section>
  </div>
</template>

<script setup lang="ts">
import { ref, computed } from 'vue'

const currentLanguage = ref<'en' | 'nl'>('en')

const copyData = {
  en: {
    hero: {
      tagline: 'AI-accelerated. Human-crafted.',
      headline: 'Scroll-stopping, sales-driving video ads built to fuel your growth.',
      subhead:
        'Turn a short brief into high-performing social videos for YouTube, TikTok and Instagram — generated fast with AI, refined by human editors, and optimised to convert viewers into customers.',
      cta1: 'Create My Ad',
      cta2: 'See Examples',
      microline: 'Fast to produce. Built to convert. Ready to sell.',
    },
    whyVideo: {
      headline: 'Why video ads?',
      stat1: 'More engagement than images',
      stat2: 'Message retention vs 10% for text',
      stat3: 'Higher landing-page conversion',
      stat4: 'Of brands say video delivers the highest ROI',
      bottomLine: 'Video is the fastest way to get attention — and turn that attention into revenue.',
    },
    quality: {
      headline: 'Built for speed. Reviewed like your sales depend on it.',
      description:
        'AI agents handle the fast work — script drafts, timing, visuals — while human editors refine everything to make sure your ad sells.',
      guarantees: [
        'Clear messaging',
        'No awkward AI phrasing',
        'No uncanny visuals',
        'Strong hooks + pacing',
        'Consistent, polished brand tone',
      ],
      microline: 'The standard isn\'t "looks good." The standard is "drives results."',
    },
    howItWorks: {
      headline: '7-Step Hybrid Pipeline',
      subhead: 'From a short brief to a sales-ready video in seven steps.',
      steps: [
        {
          title: 'Complete a 2-minute brief',
          description: 'Tell us what you sell and who you sell to.',
        },
        {
          title: 'Add your website URL',
          description: 'Agents analyse your value proposition to match tone + messaging.',
        },
        {
          title: 'Upload brand assets (optional)',
          description: 'Logos, colours, product images… or clean defaults.',
        },
        {
          title: 'AI generates a sales-focused script',
          description: 'Optimised for platform, audience and CTA.',
        },
        {
          title: 'Human refinement',
          description: 'An editor fixes phrasing, strengthens the hook, and tunes for conversions.',
        },
        {
          title: 'Automated production + human oversight',
          description: 'Voiceover, visuals, music, captions assembled for impact.',
        },
        {
          title: 'Final human approval',
          description: 'We check pacing, clarity and quality before delivery.',
        },
      ],
    },
    styles: {
      headline: 'Choose the style that sells your product best.',
      items: [
        {
          title: 'Presenter to Camera',
          description: 'trust-driven messaging',
        },
        {
          title: 'Product Showcase',
          description: 'fast, bold, perfect for e-commerce',
        },
        {
          title: 'Animated Explainer',
          description: 'clarity for apps & tools',
        },
        {
          title: 'Voiceover + B-roll',
          description: 'professional and credible',
        },
        {
          title: 'Hybrid',
          description: 'mix formats for maximum performance',
        },
      ],
    },
    durations: {
      headline: '⏱ Durations',
      items: [
        {
          title: '6s Bumper',
          description: 'Perfect for fast awareness + retargeting.',
        },
        {
          title: '15s Standard (Recommended)',
          description: 'Ideal for converting cold-to-warm viewers into buyers.',
        },
        {
          title: '30s Extended',
          description: 'Great for explaining why your offer is worth it.',
        },
      ],
    },
    pricing: {
      headline: 'Simple, transparent pricing.',
      mostPopular: 'Most Popular',
      cta: 'Get Started',
      plans: [
        {
          title: 'Starter',
          price: '€49',
          period: 'per ad',
          description: 'Sales-ready videos on a budget.',
        },
        {
          title: 'Pro',
          price: '€149',
          period: 'per month',
          description: '3 ads per month, priority production, brand kit upload.',
        },
        {
          title: 'Studio',
          price: '€499',
          period: 'per month',
          description: '10 ads per month, dedicated creative lead, multi-brand support.',
        },
      ],
    },
    faq: {
      headline: 'FAQ',
      items: [
        {
          question: 'Do your videos help drive sales?',
          answer: 'Yes — our hooks, pacing, and CTA structure are built for conversions.',
        },
        {
          question: 'Do I own the final videos?',
          answer: 'Yes. Once paid, the videos are yours.',
        },
        {
          question: 'Can I request changes?',
          answer: 'Yes — revisions included.',
        },
        {
          question: 'Are refunds available?',
          answer: 'Yes. If the second version still isn\'t right, get a full refund within 7 days.',
        },
      ],
    },
    finalCta: {
      headline: 'Ready to boost your sales with better video ads?',
      subhead: 'Start your ad now and get a conversion-ready video in minutes.',
      cta: 'Create My Ad',
    },
  },
  nl: {
    hero: {
      tagline: 'AI-versneld. Handgemaakt door experts.',
      headline: 'Video-ads die de aandacht grijpen en je groei versnellen.',
      subhead:
        'Maak van een korte briefing een krachtige social video voor YouTube, TikTok en Instagram — razendsnel gegenereerd door AI, verfijnd door menselijke editors en geoptimaliseerd om kijkers in klanten te veranderen.',
      cta1: 'Maak Mijn Advertentie',
      cta2: 'Bekijk Voorbeelden',
      microline: 'Snel gemaakt. Gebouwd om te converteren. Klaar om te verkopen.',
    },
    whyVideo: {
      headline: 'Waarom video-advertenties?',
      stat1: 'Meer engagement dan afbeeldingen',
      stat2: 'Boodschapherinnering 95% vs 10% bij tekst',
      stat3: 'Hogere conversie op landingspagina\'s',
      stat4: 'Van de merken zegt dat video de hoogste ROI levert',
      bottomLine:
        'Video is de snelste manier om aandacht te krijgen — en die aandacht om te zetten in omzet.',
    },
    quality: {
      headline: 'Gebouwd voor snelheid. Gecontroleerd alsof je omzet ervan afhangt.',
      description:
        'AI-agents doen het snelle werk — scripts, timing, visuals — terwijl menselijke editors alles verfijnen om ervoor te zorgen dat je advertentie verkoopt.',
      guarantees: [
        'Heldere boodschap',
        'Geen vreemde AI-zinnen',
        'Geen onnatuurlijke beelden',
        'Sterke hooks + tempo',
        'Consequente, professionele merktoon',
      ],
      microline: 'De norm is niet "ziet er goed uit." De norm is "levert resultaat."',
    },
    howItWorks: {
      headline: '7-Stappen Hybride Pipeline',
      subhead: 'Van een korte briefing naar een verkoopklare video in zeven stappen.',
      steps: [
        {
          title: 'Vul een briefing van 2 minuten in',
          description: 'Vertel wat je verkoopt en aan wie.',
        },
        {
          title: 'Voeg je website-URL toe',
          description: 'Agents analyseren je waardepropositie voor de juiste toon en boodschap.',
        },
        {
          title: 'Upload merkmateriaal (optioneel)',
          description: 'Logo\'s, kleuren, productfoto\'s… of wij gebruiken nette standaarden.',
        },
        {
          title: 'AI maakt een verkoopgericht script',
          description: 'Geoptimaliseerd voor platform, doelgroep en CTA.',
        },
        {
          title: 'Menselijke verfijning',
          description:
            'Een editor verbetert de tekst, versterkt de hook en optimaliseert voor conversie.',
        },
        {
          title: 'Automatische productie + menselijke controle',
          description: 'Voice-over, beelden, muziek, captions — perfect gemonteerd.',
        },
        {
          title: 'Laatste menselijke kwaliteitscheck',
          description: 'We controleren tempo, helderheid en kwaliteit vóór levering.',
        },
      ],
    },
    styles: {
      headline: 'Kies de stijl die jouw product het beste verkoopt.',
      items: [
        {
          title: 'Presentator op camera',
          description: 'betrouwbaar en direct',
        },
        {
          title: 'Product Showcase',
          description: 'snel, opvallend, ideaal voor e-commerce',
        },
        {
          title: 'Animated Explainer',
          description: 'helder voor apps & tools',
        },
        {
          title: 'Voice-over + B-roll',
          description: 'professioneel en overtuigend',
        },
        {
          title: 'Hybride',
          description: 'combineer formats voor maximale prestaties',
        },
      ],
    },
    durations: {
      headline: '⏱ Lengtes',
      items: [
        {
          title: '6s Bumper',
          description: 'Perfect voor snelle awareness + retargeting.',
        },
        {
          title: '15s Standaard (Aanbevolen)',
          description: 'Ideaal voor het omzetten van kijkers in klanten.',
        },
        {
          title: '30s Uitgebreid',
          description: 'Geweldig voor het uitleggen waarom je aanbod het waard is.',
        },
      ],
    },
    pricing: {
      headline: 'Eenvoudige, transparante prijzen.',
      mostPopular: 'Meest Populair',
      cta: 'Aan de slag',
      plans: [
        {
          title: 'Starter',
          price: '€49',
          period: 'per advertentie',
          description: 'Verkoopklare video\'s voor een klein budget.',
        },
        {
          title: 'Pro',
          price: '€149',
          period: 'per maand',
          description: '3 video\'s per maand, prioriteit, merkkit-upload.',
        },
        {
          title: 'Studio',
          price: '€499',
          period: 'per maand',
          description:
            '10 video\'s per maand, vaste creative lead, ondersteuning voor meerdere merken.',
        },
      ],
    },
    faq: {
      headline: 'Veelgestelde vragen',
      items: [
        {
          question: 'Helpen jullie video\'s echt bij verkoop?',
          answer: 'Ja — onze hooks, timing en CTA\'s zijn gebouwd voor conversie.',
        },
        {
          question: 'Ben ik eigenaar van de video\'s?',
          answer: 'Ja. Na betaling zijn ze volledig van jou.',
        },
        {
          question: 'Kan ik wijzigingen aanvragen?',
          answer: 'Ja — revisies zijn inbegrepen.',
        },
        {
          question: 'Is een terugbetaling mogelijk?',
          answer:
            'Ja. Als versie twee nog niet goed is, krijg je binnen 7 dagen geld terug.',
        },
      ],
    },
    finalCta: {
      headline: 'Klaar om je verkoop te verhogen met betere video-ads?',
      subhead: 'Begin nu en ontvang binnen enkele minuten een verkoopklare video.',
      cta: 'Maak Mijn Advertentie',
    },
  },
}

const copy = computed(() => copyData[currentLanguage.value])

useHead({
  title: 'BOM Studios - AI-Accelerated Video Ads',
  meta: [
    {
      name: 'description',
      content: 'Generate conversion-optimized video ads in minutes. AI-accelerated. Human-crafted.',
    },
  ],
})
</script>

<style scoped>
/* Language Switcher */
.language-switcher {
  position: fixed;
  top: var(--space-lg);
  right: var(--space-lg);
  z-index: 1000;
  display: flex;
  gap: var(--space-sm);
}

.lang-btn {
  padding: 0.5rem 1rem;
  background: rgba(255, 255, 255, 0.1);
  border: 1px solid var(--color-aqua-beam);
  color: var(--color-white);
  border-radius: 4px;
  cursor: pointer;
  font-size: 0.9rem;
  font-weight: 500;
  transition: all 0.3s ease;
}

.lang-btn:hover {
  background: var(--color-aqua-beam);
  color: var(--color-deep-navy);
}

.lang-btn.active {
  background: var(--color-aqua-beam);
  color: var(--color-deep-navy);
}

/* Hero */
.hero {
  min-height: 100vh;
  display: flex;
  align-items: center;
  justify-content: center;
  background: linear-gradient(135deg, var(--color-deep-navy) 0%, rgba(57, 77, 155, 0.1) 100%);
}

.hero-content {
  text-align: center;
  max-width: 800px;
}

.tagline {
  font-family: var(--font-primary);
  font-size: 1rem;
  font-weight: 600;
  color: var(--color-aqua-beam);
  margin-bottom: var(--space-lg);
  letter-spacing: 0.1em;
  text-transform: uppercase;
}

.hero h1 {
  font-size: 4rem;
  margin-bottom: var(--space-lg);
  line-height: 1.2;
  background: linear-gradient(135deg, var(--color-white) 0%, var(--color-aqua-beam) 100%);
  -webkit-background-clip: text;
  -webkit-text-fill-color: transparent;
  background-clip: text;
}

.hero-subhead {
  font-size: 1.25rem;
  margin-bottom: var(--space-xl);
  color: rgba(255, 255, 255, 0.85);
  line-height: 1.8;
}

.hero-cta {
  display: flex;
  gap: var(--space-md);
  justify-content: center;
  flex-wrap: wrap;
  margin-bottom: var(--space-2xl);
}

.microline {
  font-size: 0.95rem;
  color: var(--color-aqua-beam);
  font-weight: 500;
  letter-spacing: 0.05em;
}

/* Section Headers */
.section-header {
  margin-bottom: var(--space-2xl);
}

.section-header h2 {
  margin-bottom: var(--space-lg);
}

.section-header p {
  font-size: 1.1rem;
  color: rgba(255, 255, 255, 0.8);
}

.text-center {
  text-align: center;
}

/* Stats Grid */
.stats-grid {
  display: grid;
  grid-template-columns: repeat(4, 1fr);
  gap: var(--space-lg);
  margin-bottom: var(--space-2xl);
}

.stat-card {
  background: rgba(125, 209, 231, 0.05);
  border: 1px solid rgba(125, 209, 231, 0.2);
  padding: var(--space-xl);
  border-radius: 4px;
  text-align: center;
  transition: all 0.3s ease;
}

.stat-card:hover {
  border-color: var(--color-aqua-beam);
  background-color: rgba(125, 209, 231, 0.1);
  transform: translateY(-4px);
}

.stat-number {
  font-size: 3rem;
  font-weight: 700;
  color: var(--color-aqua-beam);
  margin-bottom: var(--space-md);
}

.stat-card p {
  font-size: 1rem;
}

.bottom-line {
  text-align: center;
  font-size: 1.2rem;
  color: rgba(255, 255, 255, 0.9);
  font-weight: 500;
}

/* Quality Section */
#quality {
  background: linear-gradient(135deg, rgba(57, 77, 155, 0.05) 0%, transparent 100%);
}

.quality-description {
  font-size: 1.15rem;
  margin-bottom: var(--space-2xl);
  line-height: 1.8;
}

.guarantees-grid {
  display: grid;
  grid-template-columns: repeat(2, 1fr);
  gap: var(--space-lg);
  margin-bottom: var(--space-2xl);
}

.guarantee-card {
  display: flex;
  gap: var(--space-md);
  align-items: flex-start;
  padding: var(--space-lg);
  background: rgba(168, 216, 151, 0.05);
  border: 1px solid rgba(168, 216, 151, 0.2);
  border-radius: 4px;
  transition: all 0.3s ease;
}

.guarantee-card:hover {
  background-color: rgba(168, 216, 151, 0.1);
  border-color: var(--color-mint-lime);
}

.guarantee-icon {
  font-size: 1.5rem;
  color: var(--color-mint-lime);
  font-weight: 700;
  flex-shrink: 0;
}

.guarantee-card h3 {
  font-size: 1.1rem;
  color: var(--color-white);
}

.quality-microline {
  text-align: center;
  font-size: 1rem;
  color: var(--color-aqua-beam);
  font-weight: 500;
}

/* Pipeline Steps */
.pipeline-steps {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(250px, 1fr));
  gap: var(--space-lg);
}

.pipeline-step {
  background: rgba(57, 77, 155, 0.1);
  border: 1px solid rgba(125, 209, 231, 0.2);
  padding: var(--space-lg);
  border-radius: 4px;
  position: relative;
  transition: all 0.3s ease;
}

.pipeline-step:hover {
  border-color: var(--color-electric-blue);
  background-color: rgba(57, 77, 155, 0.15);
  transform: translateY(-4px);
}

.step-number {
  display: inline-flex;
  align-items: center;
  justify-content: center;
  width: 48px;
  height: 48px;
  background: var(--color-electric-blue);
  color: var(--color-white);
  border-radius: 4px;
  font-weight: 700;
  font-size: 1.25rem;
  margin-bottom: var(--space-md);
}

.pipeline-step h3 {
  margin-bottom: var(--space-sm);
  font-size: 1.15rem;
}

.pipeline-step p {
  font-size: 0.95rem;
  color: rgba(255, 255, 255, 0.75);
}

/* Styles Grid */
.styles-grid {
  display: grid;
  grid-template-columns: repeat(5, 1fr);
  gap: var(--space-lg);
}

.style-card {
  text-align: center;
}

.style-card h3 {
  margin-bottom: var(--space-md);
}

/* Durations Grid */
.durations-grid {
  display: grid;
  grid-template-columns: repeat(3, 1fr);
  gap: var(--space-lg);
}

.duration-card {
  text-align: center;
}

.duration-card h3 {
  margin-bottom: var(--space-md);
}

/* Pricing */
#pricing {
  background: linear-gradient(135deg, rgba(57, 77, 155, 0.05) 0%, transparent 100%);
}

.pricing-grid {
  display: grid;
  grid-template-columns: repeat(3, 1fr);
  gap: var(--space-lg);
}

.pricing-card {
  text-align: center;
  padding: var(--space-2xl);
  display: flex;
  flex-direction: column;
  position: relative;
}

.pricing-card.featured {
  border: 2px solid var(--color-aqua-beam);
  background: rgba(125, 209, 231, 0.08);
  transform: scale(1.05);
}

.featured-badge {
  position: absolute;
  top: -12px;
  left: 50%;
  transform: translateX(-50%);
  background: var(--color-aqua-beam);
  color: var(--color-deep-navy);
  padding: 0.5rem 1rem;
  border-radius: 4px;
  font-size: 0.85rem;
  font-weight: 600;
}

.pricing-card h3 {
  margin-bottom: var(--space-lg);
  margin-top: var(--space-lg);
  font-size: 1.5rem;
}

.price {
  font-size: 2.5rem;
  font-weight: 700;
  color: var(--color-aqua-beam);
  margin-bottom: var(--space-sm);
}

.price-label {
  font-size: 0.9rem;
  color: rgba(255, 255, 255, 0.6);
  margin-bottom: var(--space-lg);
}

.price-description {
  flex-grow: 1;
  margin-bottom: var(--space-lg);
  color: rgba(255, 255, 255, 0.75);
}

.btn-full {
  width: 100%;
}

/* FAQ */
.faq-grid {
  max-width: 600px;
  margin: 0 auto;
}

.faq-item {
  background: rgba(125, 209, 231, 0.05);
  border: 1px solid rgba(125, 209, 231, 0.2);
  padding: var(--space-lg);
  border-radius: 4px;
  margin-bottom: var(--space-lg);
}

.faq-item h3 {
  margin-bottom: var(--space-md);
  color: var(--color-aqua-beam);
}

.faq-item p {
  color: rgba(255, 255, 255, 0.8);
}

/* Final CTA */
.final-cta-section {
  background: linear-gradient(135deg, var(--color-electric-blue) 0%, rgba(57, 77, 155, 0.5) 100%);
}

.final-cta-content {
  text-align: center;
  max-width: 600px;
  margin: 0 auto;
}

.final-cta-content h2 {
  margin-bottom: var(--space-lg);
  font-size: 2.5rem;
}

.final-cta-content p {
  margin-bottom: var(--space-xl);
  font-size: 1.1rem;
}

.btn-large {
  padding: var(--space-lg) 2rem;
  font-size: 1.1rem;
}

/* Responsive */
@media (max-width: 1024px) {
  .hero h1 {
    font-size: 3rem;
  }

  .stats-grid {
    grid-template-columns: repeat(2, 1fr);
  }

  .guarantees-grid {
    grid-template-columns: 1fr;
  }

  .styles-grid {
    grid-template-columns: repeat(auto-fit, minmax(200px, 1fr));
  }

  .pricing-grid {
    grid-template-columns: 1fr;
  }

  .pricing-card.featured {
    transform: scale(1);
  }

  .durations-grid {
    grid-template-columns: 1fr;
  }
}

@media (max-width: 768px) {
  .hero h1 {
    font-size: 2rem;
  }

  .hero-subhead {
    font-size: 1rem;
  }

  .hero-cta {
    flex-direction: column;
  }

  .btn {
    width: 100%;
  }

  .stats-grid {
    grid-template-columns: 1fr;
  }

  .pipeline-steps {
    grid-template-columns: 1fr;
  }

  .styles-grid {
    grid-template-columns: 1fr;
  }

  .final-cta-content h2 {
    font-size: 1.75rem;
  }
}
</style>
