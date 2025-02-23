<template>
  <header
    class="myheader sticky top-0 px-8 py-2 w-full h-24 grid grid-cols-5 items-center shadow-md"
  >
    <a id="test" href="#" class="test relative z-20 flex items-center gap-4">
      <div class="text-surface-0 text-lg font-semibold">Handwerker 1234</div>
    </a>

    <div class="col-span-3">
      <nav class="flex justify-center" role="navigation">
        <ul class="flex items-center gap-4 nav-list">
          <li
            v-for="item in menuItems"
            :key="item.id"
            class="nav-item"
            :class="[
              item.id === activeSection ? 'text-primary' : '',
              'hover:bg-blue-700 hover:text-white px-3 py-1 rounded',
            ]"
          >
            <a
              href="#"
              :class="item.id === activeSection ? 'text-primary' : ''"
              @click.prevent="item.command"
            >
              {{ item.label }}
            </a>
          </li>
        </ul>
      </nav>
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

.myheader {
  background-color: var(--p-surface-0);
}

@media (prefers-color-scheme: dark) {
  .myheader {
    background-color: var(--p-surface-900);
  }
}
</style>
