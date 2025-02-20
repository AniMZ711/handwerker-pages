<template>
  <header class="fixed px-8 py-2 w-full h-24 grid grid-cols-5 items-center">
    <a href="#" class="relative z-20 flex items-center gap-4">
      <div class="text-surface-0 text-lg font-semibold">Handwerker 1234</div>
    </a>
    <div class="flex justify-center col-span-3">
      <Menubar :model="items"> </Menubar>
    </div>
    <div class="flex justify-end">
      <Button
        severity=""
        label=" Jetzt kontaktieren"
        @click="scrollToSection('contact')"
      >
      </Button>
    </div>
  </header>
</template>

<script setup>
import { ref } from "vue";
import Menubar from "primevue/menubar";
import Button from "primevue/button";

const items = ref([
  { label: "Leistungen", command: () => scrollToSection("services") },
  { label: "Team", command: () => scrollToSection("team") },
  { label: "Referenzen", command: () => scrollToSection("references") },
  { label: "Karriere", command: () => scrollToSection("career") },
]);

const scrollToSection = (sectionId) => {
  const element = document.getElementById(sectionId);
  if (element) {
    element.scrollIntoView({ behavior: "smooth", block: "start" });
  }
};
</script>

<style scoped>
.p-menubar {
  display: flex;
  justify-content: space-around;
}

@media (max-width: 960px) {
  .p-menubar {
    display: flex;
    justify-content: end;
  }
}
</style>
