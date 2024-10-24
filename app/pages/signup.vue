<script setup lang="ts">
definePageMeta({
  layout: 'auth'
})

useSeoMeta({
  title: 'Sign up'
})

const fields = [{
  name: 'name',
  type: 'text',
  label: 'Name',
  placeholder: 'Entrez votre nom'
}, {
  name: 'email',
  type: 'email',
  label: 'Email',
  placeholder: 'Entrez votre email'
}, {
  name: 'password',
  label: 'Password',
  type: 'password',
  placeholder: 'Entrez votre mot de passe'
}]

const validate = (state: any) => {
  const errors = []
  if (!state.email) errors.push({ path: 'email', message: 'Email est requis' })
  if (!state.password) errors.push({ path: 'password', message: 'Mot de passe est requis' })
  return errors
}

const providers = [{
  label: 'Continue with GitHub',
  icon: 'i-simple-icons-github',
  color: 'gray' as const,
  click: () => {
    console.log('Rediriger vers GitHub')
  }
}]

function onSubmit(data: any) {
  console.log('Submitted', data)
}
</script>

<!-- eslint-disable vue/multiline-html-element-content-newline -->
<!-- eslint-disable vue/singleline-html-element-content-newline -->
<template>
  <UCard class="max-w-sm w-full bg-white/75 dark:bg-white/5 backdrop-blur">
    <UAuthForm
      :fields="fields"
      :validate="validate"
      :providers="providers"
      align="top"
      title="Créer un compte"
      :ui="{ base: 'text-center', footer: 'text-center' }"
      :submit-button="{ label: 'S\'inscrire' }"
      @submit="onSubmit"
    >
      <template #description>
        Vous avez déjà un compte ? <NuxtLink
          to="/login"
          class="text-primary font-medium"
        >Se connecter</NuxtLink>.
      </template>


      <template #footer>
        En vous inscrivant, vous acceptez nos <NuxtLink
          to="/"
          class="text-primary font-medium"
        >Conditions d'utilisation</NuxtLink>.
      </template>
    </UAuthForm>
  </UCard>
</template>
