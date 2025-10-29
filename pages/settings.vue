<template>
  <UPage>
    <UPageHero
      title="Account Settings"
      description="Manage your account preferences and storage"
    />

    <UContainer class="mt-8 max-w-3xl">
      <UCard>
        <template #header>
          <h2 class="text-lg font-medium">Personal Information</h2>
        </template>
        
        <UForm :state="state" @submit="onSubmit" class="space-y-6">
          <UFormGroup label="Full Name" name="name" required>
            <UInput v-model="state.name" placeholder="John Doe" />
          </UFormGroup>

          <UFormGroup label="Email" name="email" required>
            <UInput v-model="state.email" type="email" placeholder="email@example.com" />
          </UFormGroup>

          <UFormGroup label="Storage Plan" name="plan">
            <USelectMenu v-model="state.plan" :options="planOptions" />
          </UFormGroup>

          <div class="pt-4 flex justify-end">
            <UButton type="submit">Save Changes</UButton>
          </div>
        </UForm>
      </UCard>
    </UContainer>
  </UPage>
</template>

<script setup lang="ts">
interface State {
  name: string
  email: string
  plan: string
}

const state = reactive<State>({
  name: 'John Doe',
  email: 'john@example.com',
  plan: 'pro'
})

const planOptions = [
  { value: 'basic', label: 'Basic (5GB)' },
  { value: 'pro', label: 'Pro (100GB)' },
  { value: 'business', label: 'Business (500GB)' }
]

async function onSubmit(event: { data: State }) {
  console.log('Form submitted', event.data)
  // In a real app, you would send the data to an API
}
</script>