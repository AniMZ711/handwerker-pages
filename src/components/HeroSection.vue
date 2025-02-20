<template>
  <section id="hero" class="h-screen flex items-center justify-center">
    <ScrollTop />

    <div
      v-animateonscroll="{
        enterClass: 'animate-fadein',
        leaveClass: 'animate-fadeout',
      }"
      class="animate-duration-1000"
    >
      <h1 class="text-3xl font-bold">Hello!</h1>
    </div>
  </section>
</template>
