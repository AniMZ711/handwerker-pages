<script setup lang="ts">
import HeroSection from "@/components/HeroSection.vue";
import TeamSection from "@/components/TeamSection.vue";
import ServicesSection from "@/components/ServicesSection.vue";
import ContactSection from "@/components/ContactSection.vue";
import ReferencesSection from "@/components/ReferencesSection.vue";
import CareerSection from "@/components/CareerSection.vue";
</script>

<template>
  <main>
    <HeroSection id="hero" />
    <ServicesSection id="services" />
    <TeamSection id="team" />
    <ReferencesSection id="references" />
    <CareerSection id="career" />
    <ContactSection id="contact" />
  </main>
</template>
