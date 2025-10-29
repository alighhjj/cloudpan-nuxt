<template>
  <UPage>
    <UPageHero
      title="Your Files"
      description="Manage and organize your cloud storage"
    >
      <template #links>
        <UButton @click="uploadFile" size="lg" class="mr-4">
          <UIcon name="i-heroicons-arrow-up-tray" class="mr-2" />
          Upload File
        </UButton>
        <UButton @click="createFolder" size="lg" variant="outline">
          <UIcon name="i-heroicons-folder-plus" class="mr-2" />
          Create Folder
        </UButton>
      </template>
    </UPageHero>

    <div class="mt-8">
      <UTable :rows="files" :columns="columns" class="rounded-xl">
        <template #icon-data="{ row }">
          <UIcon :name="row.icon" class="h-5 w-5" />
        </template>
        <template #size-data="{ row }">
          {{ row.size ? formatFileSize(row.size) : '-' }}
        </template>
        <template #actions-data="{ row }">
          <UButton
            v-for="action in row.actions"
            :key="action.label"
            :variant="action.variant"
            :size="action.size"
            :icon="action.icon"
            @click="action.handler(row)"
          />
        </template>
      </UTable>
    </div>
  </UPage>
</template>

<script setup lang="ts">
interface File {
  id: string
  name: string
  icon: string
  size?: number
  modified: string
  type: 'file' | 'folder'
  actions: Array<{
    label: string
    variant: 'solid' | 'outline' | 'ghost'
    size: 'xs' | 'sm' | 'md' | 'lg' | 'xl'
    icon: string
    handler: (file: File) => void
  }>
}

const columns = [
  { key: 'icon', label: '', sortable: false },
  { key: 'name', label: 'Name', sortable: true },
  { key: 'size', label: 'Size', sortable: true },
  { key: 'modified', label: 'Modified', sortable: true },
  { key: 'actions', label: 'Actions', sortable: false }
]

const files: File[] = [
  {
    id: '1',
    name: 'Documents',
    icon: 'i-heroicons-folder',
    type: 'folder',
    modified: '2023-05-15',
    actions: [
      {
        label: 'Open',
        variant: 'ghost',
        size: 'sm',
        icon: 'i-heroicons-arrow-right',
        handler: (file) => console.log('Opening folder', file.name)
      }
    ]
  },
  {
    id: '2',
    name: 'Vacation_Photos.zip',
    icon: 'i-heroicons-document-text',
    size: 20485760,
    type: 'file',
    modified: '2023-06-20',
    actions: [
      {
        label: 'Download',
        variant: 'ghost',
        size: 'sm',
        icon: 'i-heroicons-arrow-down-tray',
        handler: (file) => console.log('Downloading', file.name)
      },
      {
        label: 'Share',
        variant: 'ghost',
        size: 'sm',
        icon: 'i-heroicons-share',
        handler: (file) => console.log('Sharing', file.name)
      }
    ]
  },
  {
    id: '3',
    name: 'Project_Report.pdf',
    icon: 'i-heroicons-document-text',
    size: 1048576,
    type: 'file',
    modified: '2023-07-10',
    actions: [
      {
        label: 'Download',
        variant: 'ghost',
        size: 'sm',
        icon: 'i-heroicons-arrow-down-tray',
        handler: (file) => console.log('Downloading', file.name)
      },
      {
        label: 'Share',
        variant: 'ghost',
        size: 'sm',
        icon: 'i-heroicons-share',
        handler: (file) => console.log('Sharing', file.name)
      }
    ]
  }
]

function formatFileSize(bytes: number): string {
  if (bytes === 0) return '0 Bytes'
  const k = 1024
  const sizes = ['Bytes', 'KB', 'MB', 'GB']
  const i = Math.floor(Math.log(bytes) / Math.log(k))
  return parseFloat((bytes / Math.pow(k, i)).toFixed(2)) + ' ' + sizes[i]
}

function uploadFile() {
  console.log('Uploading file')
  // Implementation would go here
}

function createFolder() {
  console.log('Creating folder')
  // Implementation would go here
}
</script>