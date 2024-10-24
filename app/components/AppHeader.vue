<template>
  <UHeader>
    <template #logo>
      ByteStudio
      <UBadge>v0.0.1</UBadge>
    </template>

    <template #right>
      <UColorModeButton size="sm" />
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
  </UHeader>
</template>
