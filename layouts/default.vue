<template>
  <div>
    <header>
      <UNavbar 
        :ui="{ wrapper: 'px-4 sm:px-6 lg:px-8' }"
        :links="navigationLinks"
      >
        <template #logo>
          <span class="font-bold">CloudPan</span>
        </template>
        
        <template #right>
          <UButton label="Sign In" color="white" variant="ghost" />
          <UButton label="Sign Up" />
        </template>
      </UNavbar>
    </header>

    <slot />

    <footer class="mt-auto py-8 px-4 sm:px-6 lg:px-8">
      <div class="max-w-7xl mx-auto">
        <UFooter 
          :links="footerLinks"
          :social-links="socialLinks"
          :ui="{ bottom: { container: 'mt-12' } }"
        />
      </div>
    </footer>
  </div>
</template>

<script setup lang="ts">
const navigationLinks = [
  { label: 'Home', to: '/' },
  { label: 'Files', to: '/files' },
  { label: 'Shared', to: '/shared' },
  { label: 'Settings', to: '/settings' }
]

const footerLinks = [
  { label: 'Terms', to: '/terms' },
  { label: 'Privacy', to: '/privacy' },
  { label: 'Security', to: '/security' },
  { label: 'Status', to: '/status' }
]

const socialLinks = [
  { icon: 'i-simple-icons-github', to: 'https://github.com/nuxt-ui-pro' },
  { icon: 'i-simple-icons-twitter', to: 'https://twitter.com/nuxt_js' }
]
</script>