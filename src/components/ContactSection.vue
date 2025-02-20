<script lang="ts"></script>

<template>
  <section
    id="contact"
    class="h-screen flex flex-col items-center justify-center"
  >
    <ScrollTop />

    <div
      v-animateonscroll="{
        enterClass: 'animate-fadein',
        leaveClass: 'animate-fadeout',
      }"
      class="animate-duration-1000"
    >
      <h1 class="text-3xl font-bold">Contact Us</h1>
    </div>
  </section>
</template>
