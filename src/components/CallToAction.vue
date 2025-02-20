<script setup lang="ts"></script>

<template>
  <section id="callToAction" class="h-screen flex items-center justify-center">
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
