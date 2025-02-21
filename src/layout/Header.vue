<template>
  <header
    class="fixed px-8 py-2 w-full h-24 grid grid-cols-5 items-center shadow-md"
  >
    <a href="#" class="relative z-20 flex items-center gap-4">
      <div class="text-surface-0 text-lg font-semibold">Handwerker 1234</div>
    </a>
    <div class="flex justify-center col-span-3">
      <Menubar :model="menuItems">
        <template #item="{ item }">
          <a
            :class="item.id === activeSection ? 'text-primary' : ''"
            @click="item.command"
          >
            {{ item.label }}
          </a>
        </template>
      </Menubar>
    </div>
    <div class="flex justify-end">
      <Button label="Jetzt kontaktieren" @click="scrollToSection('contact')">
      </Button>
    </div>
  </header>
</template>

<script setup>
import { ref, onMounted, onUnmounted, computed } from "vue";
import Menubar from "primevue/menubar";
import Button from "primevue/button";

const activeSection = ref("hero");

const sections = [
  { id: "hero", label: "Home" },
  { id: "services", label: "Leistungen" },
  { id: "team", label: "Team" },
  { id: "references", label: "Referenzen" },
  { id: "career", label: "Karriere" },
  { id: "contact", label: "Kontakt" },
];
const menuItems = computed(() =>
  sections.map((section) => ({
    label: section.label,
    command: () => scrollToSection(section.id),
    id: section.id,
  }))
);

const scrollToSection = (sectionId) => {
  const element = document.getElementById(sectionId);
  if (element) {
    element.scrollIntoView({ behavior: "smooth", block: "start" });
  }
};

const updateActiveSection = () => {
  let scrollPosition = window.scrollY;

  sections.forEach((section) => {
    const element = document.getElementById(section.id);
    if (element) {
      const offset = element.offsetTop - 150;
      const height = element.offsetHeight;
      if (scrollPosition >= offset && scrollPosition < offset + height) {
        activeSection.value = section.id;
        console.log(section.id);
      }
    } else {
      activeSection.value = "";
    }
  });
};

onMounted(() => {
  window.addEventListener("scroll", updateActiveSection);
});

onUnmounted(() => {
  window.removeEventListener("scroll", updateActiveSection);
});
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
