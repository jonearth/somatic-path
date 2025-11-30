---
type: "hero"
headline: "Move Through Life with Ease. A Method Built for Learning."
subheadline: "We are built to move, learn, and improve—at any age. Whether you are recovering from injury, managing stress, or seeking peak performance, Awareness Through Movement® offers a scientifically proven path to unlock your potential. Don't just endure life; move through it."
cta_text: "Discover the Method"
image_url: ""
---

{{- $page := . -}}
<section id="hero" class="relative min-h-screen flex items-center justify-center overflow-hidden">
    <!-- Background Image -->
    <div class="absolute inset-0 z-0">
        <img 
            src="/images/hero.jpg"
            alt="{{ .Params.hero_alt | default "Feldenkrais Method" }}"
            class="w-full h-full object-cover">
        <!-- Dark overlay for text readability -->
        <div class="absolute inset-0 bg-felden-green/60"></div>
    </div>
    
    <!-- Content -->
    <div class="relative z-10 max-w-4xl mx-auto px-6 text-center text-white">
        <h1 class="font-serif text-4xl md:text-5xl lg:text-6xl font-bold mb-6 leading-tight">
            {{ .Params.headline }}
        </h1>
        
        {{ with .Params.subheadline }}
        <p class="font-serif text-xl md:text-2xl lg:text-3xl mb-6 text-felden-sand">
            {{ . }}
        </p>
        {{ end }}
        
        {{ with .Params.description }}
        <p class="text-lg md:text-xl mb-10 max-w-2xl mx-auto leading-relaxed opacity-90">
            {{ . }}
        </p>
        {{ end }}
        
        {{ with .Params.cta_text }}
        <a href="{{ $.Params.cta_url | default "#services" }}" 
           class="inline-block bg-felden-terra hover:bg-felden-terra/90 text-white font-semibold py-4 px-10 rounded-full text-lg transition-all duration-300 hover:scale-105">
            {{ . }}
        </a>
        {{ end }}
    </div>
    
    <!-- Scroll indicator -->
    <div class="absolute bottom-8 left-1/2 transform -translate-x-1/2 z-10 animate-bounce">
        <svg class="w-8 h-8 text-white/70" fill="none" stroke="currentColor" viewBox="0 0 24 24">
            <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M19 14l-7 7m0 0l-7-7m7 7V3"/>
        </svg>
    </div>
</section>
