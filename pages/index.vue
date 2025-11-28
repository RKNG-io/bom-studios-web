<template>
  <div>
    <!-- Language Switcher -->
    <div class="lang-switcher">
      <button
        :class="['lang-btn', { active: currentLanguage === 'en' }]"
        @click="currentLanguage = 'en'"
      >
        EN
      </button>
      <button
        :class="['lang-btn', { active: currentLanguage === 'nl' }]"
        @click="currentLanguage = 'nl'"
      >
        NL
      </button>
    </div>

    <!-- Hero Section -->
    <section class="hero" id="hero">
      <div class="warp-bg">
        <div class="speed-streaks"></div>
      </div>
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
      <!-- Background logo watermark -->
      <img src="~/assets/images/BOM.png" alt="" class="hero-logo-bg" aria-hidden="true" />
    </section>

    <div class="pixel-divider"></div>

    <!-- Why Video Section -->
    <section id="why-video">
      <div class="container">
        <h2 class="text-center mb-6">{{ copy.whyVideo.headline }}</h2>
        <div class="stats-grid">
          <div class="stat-card">
            <div class="stat-number">3x</div>
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
        <p class="bottom-line">{{ copy.whyVideo.bottomLine }}</p>
      </div>
    </section>

    <div class="pixel-divider"></div>

    <!-- Quality Section (Two-Column) -->
    <section id="quality">
      <div class="container">
        <div class="quality-grid">
          <div class="quality-copy">
            <h2>{{ copy.quality.headline }}</h2>
            <p>{{ copy.quality.description }}</p>
            <p class="microline mt-4">{{ copy.quality.microline }}</p>
          </div>
          <div class="quality-checklist">
            <div class="check-item" v-for="(guarantee, index) in copy.quality.guarantees" :key="index">
              <span class="check-icon">&#10003;</span>
              <span>{{ guarantee }}</span>
            </div>
          </div>
        </div>
      </div>
    </section>

    <div class="pixel-divider"></div>

    <!-- How It Works Section -->
    <section id="how-it-works">
      <div class="container">
        <h2 class="text-center mb-4">{{ copy.howItWorks.headline }}</h2>
        <p class="text-center mb-6 subhead">{{ copy.howItWorks.subhead }}</p>

        <div class="pipeline-grid">
          <div class="pipeline-step" v-for="(step, index) in copy.howItWorks.steps" :key="index">
            <div class="step-number">{{ String(index + 1).padStart(2, '0') }}</div>
            <h3>{{ step.title }}</h3>
            <p>{{ step.description }}</p>
          </div>
        </div>
      </div>
    </section>

    <div class="pixel-divider"></div>

    <!-- Video Styles Section -->
    <section id="video-styles">
      <div class="container">
        <h2 class="text-center mb-6">{{ copy.styles.headline }}</h2>
        <div class="styles-grid">
          <div class="style-card card" v-for="(style, index) in copy.styles.items" :key="index">
            <h3>{{ style.title }}</h3>
            <p>{{ style.description }}</p>
          </div>
        </div>
      </div>
    </section>

    <div class="pixel-divider"></div>

    <!-- Durations Section -->
    <section id="durations">
      <div class="container">
        <h2 class="text-center mb-6">{{ copy.durations.headline }}</h2>
        <div class="durations-grid">
          <div class="duration-card card" v-for="(duration, index) in copy.durations.items" :key="index">
            <h3>{{ duration.title }}</h3>
            <p>{{ duration.description }}</p>
          </div>
        </div>
      </div>
    </section>

    <div class="pixel-divider"></div>

    <!-- Pricing Section -->
    <section id="pricing">
      <div class="container">
        <h2 class="text-center mb-6">{{ copy.pricing.headline }}</h2>
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
            <p class="price-period">{{ plan.period }}</p>
            <p class="price-description">{{ plan.description }}</p>
            <button class="btn btn-primary btn-full">{{ copy.pricing.cta }}</button>
          </div>
        </div>
      </div>
    </section>

    <div class="pixel-divider"></div>

    <!-- FAQ Section (Accordion) -->
    <section id="faq">
      <div class="container">
        <h2 class="text-center mb-6">{{ copy.faq.headline }}</h2>
        <div class="faq-list">
          <div
            class="faq-item"
            :class="{ active: activeFaq === index }"
            v-for="(item, index) in copy.faq.items"
            :key="index"
          >
            <button class="faq-question" @click="toggleFaq(index)">
              <span>{{ item.question }}</span>
              <span class="faq-icon">+</span>
            </button>
            <div class="faq-answer">
              <p>{{ item.answer }}</p>
            </div>
          </div>
        </div>
      </div>
    </section>

    <div class="pixel-divider"></div>

    <!-- Final CTA Section -->
    <section id="final-cta" class="final-cta">
      <div class="warp-bg">
        <div class="speed-streaks"></div>
      </div>
      <div class="container relative z-1">
        <h2>{{ copy.finalCta.headline }}</h2>
        <p>{{ copy.finalCta.subhead }}</p>
        <button class="btn btn-primary btn-large">{{ copy.finalCta.cta }}</button>
      </div>
    </section>
  </div>
</template>

<script setup lang="ts">
import { ref, computed } from 'vue'

const currentLanguage = ref<'en' | 'nl'>('en')
const activeFaq = ref<number | null>(null)

const toggleFaq = (index: number) => {
  activeFaq.value = activeFaq.value === index ? null : index
}

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
      headline: 'Automation for speed. Craftsmanship for results.',
      description:
        'AI agents generate drafts, but real editors fix phrasing, pacing, tone, visuals and timing — so your video actually sells.',
      guarantees: [
        'No uncanny visuals',
        'No awkward phrasing',
        'No weird pacing',
        'Consistent brand tone',
        'Performance-focused hooks',
        'Sales-ready delivery',
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
          description: 'Logos, colours, product images... or clean defaults.',
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
          title: 'Talking Head',
          description: 'Trust-driven messaging',
        },
        {
          title: 'Product Showcase',
          description: 'Fast, bold, perfect for e-commerce',
        },
        {
          title: 'Animated Explainer',
          description: 'Clarity for apps & tools',
        },
        {
          title: 'Voiceover + B-roll',
          description: 'Professional and credible',
        },
        {
          title: 'Hybrid',
          description: 'Mix formats for maximum performance',
        },
      ],
    },
    durations: {
      headline: 'Pick your duration',
      items: [
        {
          title: '6s Bumper',
          description: 'Perfect for fast awareness + retargeting.',
        },
        {
          title: '15s Standard',
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
      headline: 'Automatisering voor snelheid. Vakmanschap voor resultaat.',
      description:
        'AI-agents maken concepten, maar echte editors verbeteren tekst, timing, toon, beelden en ritme — zodat je video daadwerkelijk verkoopt.',
      guarantees: [
        'Geen onnatuurlijke beelden',
        'Geen vreemde zinnen',
        'Geen rare timing',
        'Consistente merktoon',
        'Prestatiegerichte hooks',
        'Verkoopklare levering',
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
          description: 'Logo\'s, kleuren, productfoto\'s... of wij gebruiken nette standaarden.',
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
          description: 'We controleren tempo, helderheid en kwaliteit voor levering.',
        },
      ],
    },
    styles: {
      headline: 'Kies de stijl die jouw product het beste verkoopt.',
      items: [
        {
          title: 'Talking Head',
          description: 'Betrouwbaar en direct',
        },
        {
          title: 'Product Showcase',
          description: 'Snel, opvallend, ideaal voor e-commerce',
        },
        {
          title: 'Animated Explainer',
          description: 'Helder voor apps & tools',
        },
        {
          title: 'Voice-over + B-roll',
          description: 'Professioneel en overtuigend',
        },
        {
          title: 'Hybride',
          description: 'Combineer formats voor maximale prestaties',
        },
      ],
    },
    durations: {
      headline: 'Kies je lengte',
      items: [
        {
          title: '6s Bumper',
          description: 'Perfect voor snelle awareness + retargeting.',
        },
        {
          title: '15s Standaard',
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
/* Subhead styling */
.subhead {
  font-size: 1.1rem;
  color: rgba(255, 255, 255, 0.75);
  max-width: 600px;
  margin-left: auto;
  margin-right: auto;
}
</style>
