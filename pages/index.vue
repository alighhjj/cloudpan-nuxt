<template>
  <UPage>
    <UPageHero
      title="Welcome to CloudPan"
      description="A modern, secure, and efficient cloud storage solution built with Nuxt and Nuxt UI."
      :ui="{ base: 'items-center text-center', description: 'text-lg max-w-2xl mx-auto' }"
    >
      <template #links>
        <UButton to="/files" size="lg" class="mr-4">Access Files</UButton>
        <UButton to="/about" size="lg" variant="outline">Learn More</UButton>
      </template>
    </UPageHero>

    <UPageGrid>
      <UPageCard title="Upload Files" description="Securely upload your files to the cloud">
        <UAvatar size="xl" :src="`https://placehold.co/400x400?text=U`" alt="Upload" class="mb-4" />
        <p class="text-sm text-gray-500 dark:text-gray-400">Drag & drop files or click to upload</p>
      </UPageCard>

      <UPageCard title="Share Securely" description="Share your files with others via secure links">
        <UAvatar size="xl" :src="`https://placehold.co/400x400?text=S`" alt="Share" class="mb-4" />
        <p class="text-sm text-gray-500 dark:text-gray-400">Control access with password protection</p>
      </UPageCard>

      <UPageCard title="Access Anywhere" description="Access your files from any device">
        <UAvatar size="xl" :src="`https://placehold.co/400x400?text=A`" alt="Access" class="mb-4" />
        <p class="text-sm text-gray-500 dark:text-gray-400">Available on web, mobile, and desktop</p>
      </UPageCard>
    </UPageGrid>
  </UPage>
</template>