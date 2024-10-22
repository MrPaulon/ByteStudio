<script setup lang="ts">
import type { NavItem } from '@nuxt/content'

const navigation = inject<Ref<NavItem[]>>('navigation', ref([]))

const links = [{
  label: 'Explorer',
  to: '/explore'
},{
  label: 'Docs',
  to: '/docs'
}, {
  label: 'Abonnements',
  to: '/pricing'
}, {
  label: 'Blog',
  to: '/blog'
}]
</script>

<template>
  <UHeader :links="links">
    <template #logo>
      Code App
      <UBadge>v0.0.1</UBadge>
    </template>

    <template #right>
      <UButton
        label="Se connecter"
        color="gray"
        to="/login"
      />
      <UButton
        label="S'inscrire"
        icon="i-heroicons-arrow-right-20-solid"
        trailing
        color="black"
        to="/signup"
        class="hidden lg:flex"
      />
    </template>

    <template #panel>
      <UNavigationTree
        :links="mapContentNavigation(navigation)"
        default-open
      />
    </template>
  </UHeader>
</template>
