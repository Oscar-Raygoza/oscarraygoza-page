<template>
  <div>
    <header class="flex items-center mb-6 h-20">
      <div class="container flex items-center justify-between">
        <div class="app-logo">
          <g-link to="/">
              <img
                class="img-logo"
                src="@/assets/images/logo.png"
                alt="Oscar Raygoza Logo"
              />
          </g-link>
        </div>
        <Navbar />
        <ThemeToggle />
      </div>
    </header>
    <section class="hero is-medium is-primary">
      <div class="hero-body">
        <div class="container">
          <h1 class="title is-1">
            {{ pageTitle }}
          </h1>
          <h2 v-if="pageSubtitle" class="subtitle">
            {{ pageSubtitle }}
          </h2>
        </div>
      </div>
    </section>
    <main>
      <slot />
    </main>
  </div>
</template>

<static-query>
query {
  metadata {
    siteName
  }
}
</static-query>

<script>
import Navbar from '../components/Navbar';
import ThemeToggle from '@/components/ThemeToggle.vue';
export default {
  props: { pageTitle: '', pageSubtitle: '', color: '' },
  components: { Navbar, ThemeToggle },
};
</script>

<style lang="scss">
body {
  font-family: -apple-system, system-ui, BlinkMacSystemFont, 'Segoe UI', Roboto, 'Helvetica Neue',
    Arial, sans-serif;
  margin: 0;
  padding: 0;
  line-height: 1.5;
}
</style>
