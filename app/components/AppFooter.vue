<script setup lang="ts">
const links = [{
  label: 'Ressources',
  children: [{
    label: 'Centre d\'aide'
  }, {
    label: 'Docs'
  }, {
    label: 'Changelog'
  }]
}, {
  label: 'Réseaux',
  children: [{
    label: 'Discord'
  }, {
    label: 'Twitter'
  }, {
    label: 'Linkedin'
  }, {
    label: 'Instagram'
  }]
}]

const toast = useToast()

const email = ref('')
const loading = ref(false)

function onSubmit() {
  loading.value = true

  setTimeout(() => {
    toast.add({
      title: 'Abonné !',
      description: 'Vous êtes abonné à notre newsletter.'
    })

    loading.value = false
  }, 1000)
}
</script>

<template>
  <UFooter>
    <template #top>
      <UFooterColumns :links="links">
        <template #right>
          <form @submit.prevent="onSubmit">
            <UFormGroup
              label="S'abonner à notre newsletter"
              :ui="{ container: 'mt-3' }"
            >
              <UInput
                v-model="email"
                type="email"
                placeholder="Entrez votre email"
                :ui="{ icon: { trailing: { pointer: '' } } }"
                required
                size="xl"
                autocomplete="off"
                class="max-w-sm"
                input-class="rounded-full"
              >
                <template #trailing>
                  <UButton
                    type="submit"
                    size="xs"
                    color="primary"
                    :label="loading ? 'S\'abonner' : 'S\'abonner'"
                    :loading="loading"
                  />
                </template>
              </UInput>
            </UFormGroup>
          </form>
        </template>
      </UFooterColumns>
    </template>

    <template #left>
      <p class="text-gray-500 dark:text-gray-400 text-sm">
        Copyright ByteStudio © {{ new Date().getFullYear() }}. Tous droits réservés.
      </p>
    </template>

    <template #right>
      <UColorModeButton size="sm" />

      <UButton
        to="https://github.com/nuxt-ui-pro/saas"
        target="_blank"
        icon="i-simple-icons-github"
        aria-label="GitHub"
        color="gray"
        variant="ghost"
      />
    </template>
  </UFooter>
</template>
